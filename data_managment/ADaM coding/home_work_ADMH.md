Сборка ADMH
================
Касьянова Мария
2024-11-10

``` r
med_his <- read.xlsx("./SDTM/MH_MEDICALHISTORY.xlsx")

ADSL <- read.xlsx("./ADaM-like/ADSL.xlsx")
```

``` r
from_adsl <- ADSL %>% 
  select(STUDYID, USUBJID, TRTP, TRTPN) 

summary(from_adsl)
```

    ##    STUDYID            USUBJID              TRTP               TRTPN    
    ##  Length:4           Length:4           Length:4           Min.   :1.0  
    ##  Class :character   Class :character   Class :character   1st Qu.:1.0  
    ##  Mode  :character   Mode  :character   Mode  :character   Median :1.5  
    ##                                                           Mean   :1.5  
    ##                                                           3rd Qu.:2.0  
    ##                                                           Max.   :2.0

``` r
new_date <- function(string){
  if(is.na(string) | string == ""){
    return("")
  }
  if (length(str_split_1(string, "-")) == 1){
    string <- paste(string, "-01-01", sep = "")
  }
  else if (length(str_split_1(string, "-")) == 2){
    string <- paste(string, "-01", sep = "")
  }
  return(format(as.Date(string, format = "%Y-%m-%d"), "%d.%m.%Y"))
}

datefl <- function(string){
  if(is.na(string) | string == ""){
    return("Y")
  }
  if (length(str_split_1(string, "-")) == 1){
    return("M")
  }
  else if (length(str_split_1(string, "-")) == 2){
    return("D")
  }
  return("")
}


from_med_his <- 
  med_his %>% 
  select(STUDYID, SUBJID, MHSEQ, MHCAT, MHTERM,
         MHDECOD, MHBODSYS, MHSTDTC,
         MHENRTPT, MHENDTC) %>% 
  filter(MHCAT == "Medical History",
         MHTERM != "") %>%
  mutate(USUBJID = paste(STUDYID, SUBJID, sep = '-'),
         MHSEQ = as.numeric(MHSEQ),
         ASTDT = map(MHSTDTC, new_date),
         ASTDTF = map(MHSTDTC, datefl), 
         MHENRF = replace(MHENRTPT, MHENRTPT != "ONGOING", ""),
         AENDT = replace(map(MHENDTC, new_date), MHENRTPT == "ONGOING", ""),
         AENDTF = map(MHENDTC, datefl))
```

``` r
ADMH <- left_join(from_med_his, from_adsl)%>% 
  select(STUDYID, 
         USUBJID,
         TRTP,
         TRTPN,
         MHSEQ,
         MHCAT, 
         MHTERM,
         MHDECOD, 
         MHBODSYS, 
         MHSTDTC,
         ASTDT,
         ASTDTF,
         MHENDTC,
         AENDT,
         AENDTF,
         MHENRTPT,
         MHENRF)
```

    ## Joining with `by = join_by(STUDYID, USUBJID)`

``` r
write.xlsx(ADMH, "./ADaM-like/ADMH.xlsx")
```
