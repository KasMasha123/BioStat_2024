ДЗ по автоматизации данных в R
================
Касьянова Мария
2024-10-27

# Чтение данных

В вашем варианте нужно использовать датасет food.

``` r
food <- read.csv("./data/raw/food.csv")
```

# Выведите общее описание данных

Информцию про датасет можно найти по ссылке:
<https://www.kaggle.com/datasets/mexwell/food-vitamins-minerals-macronutrient>.
Большинство переменных являются количественными. Посмотрим на краткую
характеристику:

``` r
glimpse(food)
```

    ## Rows: 7,083
    ## Columns: 38
    ## $ Category                       <chr> "Milk", "Milk", "Milk", "Milk", "Milk",~
    ## $ Description                    <chr> "Milk, human", "Milk, NFS", "Milk, whol~
    ## $ Nutrient.Data.Bank.Number      <int> 11000000, 11100000, 11111000, 11111100,~
    ## $ Data.Alpha.Carotene            <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ~
    ## $ Data.Beta.Carotene             <int> 7, 4, 7, 7, 7, 1, 0, 3, 1, 3, 1, 2, 1, ~
    ## $ Data.Beta.Cryptoxanthin        <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ~
    ## $ Data.Carbohydrate              <dbl> 6.89, 4.87, 4.67, 4.46, 4.67, 5.19, 4.8~
    ## $ Data.Cholesterol               <int> 14, 8, 12, 14, 12, 5, 2, 8, 5, 8, 5, 3,~
    ## $ Data.Choline                   <dbl> 16.0, 17.9, 17.8, 16.0, 17.8, 17.4, 16.~
    ## $ Data.Fiber                     <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ~
    ## $ Data.Lutein.and.Zeaxanthin     <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ~
    ## $ Data.Lycopene                  <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ~
    ## $ Data.Niacin                    <dbl> 0.177, 0.110, 0.105, 0.043, 0.105, 0.11~
    ## $ Data.Protein                   <dbl> 1.03, 3.34, 3.28, 3.10, 3.28, 3.38, 3.4~
    ## $ Data.Retinol                   <int> 60, 58, 31, 28, 31, 58, 137, 83, 58, 83~
    ## $ Data.Riboflavin                <dbl> 0.036, 0.137, 0.138, 0.105, 0.138, 0.14~
    ## $ Data.Selenium                  <dbl> 1.8, 1.9, 1.9, 2.0, 1.9, 2.1, 2.1, 1.8,~
    ## $ Data.Sugar.Total               <dbl> 6.89, 4.89, 4.81, 4.46, 4.81, 4.96, 4.8~
    ## $ Data.Thiamin                   <dbl> 0.014, 0.057, 0.056, 0.020, 0.056, 0.05~
    ## $ Data.Water                     <dbl> 87.50, 89.04, 88.10, 88.20, 88.10, 89.7~
    ## $ Data.Fat.Monosaturated.Fat     <dbl> 1.658, 0.426, 0.688, 0.999, 0.688, 0.21~
    ## $ Data.Fat.Polysaturated.Fat     <dbl> 0.497, 0.065, 0.108, 0.128, 0.108, 0.03~
    ## $ Data.Fat.Saturated.Fat         <dbl> 2.009, 1.164, 1.860, 2.154, 1.860, 0.56~
    ## $ Data.Fat.Total.Lipid           <dbl> 4.38, 1.99, 3.20, 3.46, 3.20, 0.95, 0.1~
    ## $ Data.Major.Minerals.Calcium    <int> 32, 126, 123, 101, 123, 126, 204, 126, ~
    ## $ Data.Major.Minerals.Copper     <dbl> 0.052, 0.001, 0.001, 0.010, 0.001, 0.00~
    ## $ Data.Major.Minerals.Iron       <dbl> 0.03, 0.00, 0.00, 0.05, 0.00, 0.00, 0.0~
    ## $ Data.Major.Minerals.Magnesium  <int> 3, 12, 12, 5, 12, 12, 11, 12, 12, 12, 1~
    ## $ Data.Major.Minerals.Phosphorus <int> 14, 103, 101, 86, 101, 103, 101, 103, 1~
    ## $ Data.Major.Minerals.Potassium  <int> 51, 157, 150, 253, 150, 159, 166, 159, ~
    ## $ Data.Major.Minerals.Sodium     <int> 17, 39, 38, 3, 38, 39, 52, 39, 39, 39, ~
    ## $ Data.Major.Minerals.Zinc       <dbl> 0.17, 0.42, 0.41, 0.38, 0.41, 0.43, 0.4~
    ## $ Data.Vitamins.Vitamin.A...RAE  <int> 61, 59, 32, 29, 32, 58, 137, 83, 58, 83~
    ## $ Data.Vitamins.Vitamin.B12      <dbl> 0.05, 0.56, 0.54, 0.36, 0.54, 0.61, 0.3~
    ## $ Data.Vitamins.Vitamin.B6       <dbl> 0.011, 0.060, 0.061, 0.034, 0.061, 0.06~
    ## $ Data.Vitamins.Vitamin.C        <dbl> 5.0, 0.1, 0.0, 0.9, 0.0, 0.0, 1.0, 0.2,~
    ## $ Data.Vitamins.Vitamin.E        <dbl> 0.08, 0.03, 0.05, 0.08, 0.05, 0.02, 0.0~
    ## $ Data.Vitamins.Vitamin.K        <dbl> 0.3, 0.2, 0.3, 0.3, 0.3, 0.1, 0.0, 0.2,~

Также можно узнать чуть больше при помощи функции summary:

``` r
summary(food)
```

    ##    Category         Description        Nutrient.Data.Bank.Number
    ##  Length:7083        Length:7083        Min.   :11000000         
    ##  Class :character   Class :character   1st Qu.:27150770         
    ##  Mode  :character   Mode  :character   Median :53260200         
    ##                                        Mean   :48849646         
    ##                                        3rd Qu.:67203450         
    ##                                        Max.   :99998210         
    ##  Data.Alpha.Carotene Data.Beta.Carotene Data.Beta.Cryptoxanthin
    ##  Min.   :   0.00     Min.   :    0.0    Min.   :   0.000       
    ##  1st Qu.:   0.00     1st Qu.:    0.0    1st Qu.:   0.000       
    ##  Median :   0.00     Median :    8.0    Median :   0.000       
    ##  Mean   :  43.76     Mean   :  255.4    Mean   :   4.862       
    ##  3rd Qu.:   1.00     3rd Qu.:   73.0    3rd Qu.:   1.000       
    ##  Max.   :4655.00     Max.   :14134.0    Max.   :1922.000       
    ##  Data.Carbohydrate Data.Cholesterol   Data.Choline      Data.Fiber    
    ##  Min.   :  0.00    Min.   :   0.00   Min.   :  0.00   Min.   : 0.000  
    ##  1st Qu.:  5.65    1st Qu.:   0.00   1st Qu.: 10.00   1st Qu.: 0.100  
    ##  Median : 13.30    Median :   8.00   Median : 19.60   Median : 1.000  
    ##  Mean   : 20.83    Mean   :  34.46   Mean   : 34.44   Mean   : 1.704  
    ##  3rd Qu.: 26.20    3rd Qu.:  46.00   3rd Qu.: 44.20   3rd Qu.: 2.100  
    ##  Max.   :100.00    Max.   :3074.00   Max.   :820.20   Max.   :46.200  
    ##  Data.Lutein.and.Zeaxanthin Data.Lycopene      Data.Niacin     
    ##  Min.   :    0.0            Min.   :    0.0   Min.   :  0.000  
    ##  1st Qu.:    0.0            1st Qu.:    0.0   1st Qu.:  0.535  
    ##  Median :   18.0            Median :    0.0   Median :  1.487  
    ##  Mean   :  213.4            Mean   :  263.6   Mean   :  2.647  
    ##  3rd Qu.:   81.0            3rd Qu.:    0.0   3rd Qu.:  3.400  
    ##  Max.   :15643.0            Max.   :45902.0   Max.   :127.500  
    ##   Data.Protein     Data.Retinol     Data.Riboflavin   Data.Selenium    
    ##  Min.   : 0.000   Min.   :   0.00   Min.   : 0.0000   Min.   :   0.00  
    ##  1st Qu.: 2.220   1st Qu.:   0.00   1st Qu.: 0.0600   1st Qu.:   1.70  
    ##  Median : 6.190   Median :   8.00   Median : 0.1240   Median :   8.10  
    ##  Mean   : 8.599   Mean   :  49.83   Mean   : 0.1888   Mean   :  13.09  
    ##  3rd Qu.:12.130   3rd Qu.:  43.00   3rd Qu.: 0.2200   3rd Qu.:  20.00  
    ##  Max.   :78.130   Max.   :9349.00   Max.   :17.5000   Max.   :1917.00  
    ##  Data.Sugar.Total  Data.Thiamin       Data.Water    Data.Fat.Monosaturated.Fat
    ##  Min.   : 0.000   Min.   : 0.0000   Min.   : 0.00   Min.   : 0.000            
    ##  1st Qu.: 0.780   1st Qu.: 0.0400   1st Qu.:45.90   1st Qu.: 0.513            
    ##  Median : 2.390   Median : 0.0870   Median :66.59   Median : 1.869            
    ##  Mean   : 7.337   Mean   : 0.1714   Mean   :59.80   Mean   : 3.218            
    ##  3rd Qu.: 7.380   3rd Qu.: 0.1890   3rd Qu.:80.61   3rd Qu.: 4.433            
    ##  Max.   :99.800   Max.   :23.3750   Max.   :99.98   Max.   :75.221            
    ##  Data.Fat.Polysaturated.Fat Data.Fat.Saturated.Fat Data.Fat.Total.Lipid
    ##  Min.   : 0.000             Min.   : 0.000         Min.   :  0.000     
    ##  1st Qu.: 0.338             1st Qu.: 0.503         1st Qu.:  2.060     
    ##  Median : 1.036             Median : 1.444         Median :  5.480     
    ##  Mean   : 2.174             Mean   : 2.795         Mean   :  8.958     
    ##  3rd Qu.: 2.625             3rd Qu.: 3.668         3rd Qu.: 12.650     
    ##  Max.   :67.849             Max.   :82.500         Max.   :100.000     
    ##  Data.Major.Minerals.Calcium Data.Major.Minerals.Copper
    ##  Min.   :   0.00             Min.   : 0.0000           
    ##  1st Qu.:  14.00             1st Qu.: 0.0500           
    ##  Median :  37.00             Median : 0.0790           
    ##  Mean   :  73.47             Mean   : 0.1416           
    ##  3rd Qu.:  92.00             3rd Qu.: 0.1280           
    ##  Max.   :1375.00             Max.   :14.4660           
    ##  Data.Major.Minerals.Iron Data.Major.Minerals.Magnesium
    ##  Min.   : 0.000           Min.   :  0.00               
    ##  1st Qu.: 0.460           1st Qu.: 12.00               
    ##  Median : 1.040           Median : 20.00               
    ##  Mean   : 1.752           Mean   : 27.79               
    ##  3rd Qu.: 1.840           3rd Qu.: 29.00               
    ##  Max.   :64.100           Max.   :611.00               
    ##  Data.Major.Minerals.Phosphorus Data.Major.Minerals.Potassium
    ##  Min.   :   0.0                 Min.   :   0.0               
    ##  1st Qu.:  48.0                 1st Qu.: 111.0               
    ##  Median : 102.0                 Median : 183.0               
    ##  Mean   : 133.1                 Mean   : 217.1               
    ##  3rd Qu.: 189.0                 3rd Qu.: 270.5               
    ##  Max.   :1429.0                 Max.   :6040.0               
    ##  Data.Major.Minerals.Sodium Data.Major.Minerals.Zinc
    ##  Min.   :   0.0             Min.   : 0.000          
    ##  1st Qu.: 124.0             1st Qu.: 0.360          
    ##  Median : 313.0             Median : 0.680          
    ##  Mean   : 340.5             Mean   : 1.281          
    ##  3rd Qu.: 454.0             3rd Qu.: 1.360          
    ##  Max.   :7851.0             Max.   :98.860          
    ##  Data.Vitamins.Vitamin.A...RAE Data.Vitamins.Vitamin.B12
    ##  Min.   :   0.00               Min.   : 0.0000          
    ##  1st Qu.:   2.00               1st Qu.: 0.0000          
    ##  Median :  20.00               Median : 0.1800          
    ##  Mean   :  73.14               Mean   : 0.7052          
    ##  3rd Qu.:  61.00               3rd Qu.: 0.5500          
    ##  Max.   :9363.00               Max.   :82.4400          
    ##  Data.Vitamins.Vitamin.B6 Data.Vitamins.Vitamin.C Data.Vitamins.Vitamin.E
    ##  Min.   : 0.0000          Min.   :  0.000         Min.   :  0.000        
    ##  1st Qu.: 0.0520          1st Qu.:  0.000         1st Qu.:  0.230        
    ##  Median : 0.1100          Median :  0.700         Median :  0.550        
    ##  Mean   : 0.1975          Mean   :  5.696         Mean   :  1.087        
    ##  3rd Qu.: 0.2030          3rd Qu.:  5.300         3rd Qu.:  1.110        
    ##  Max.   :12.0000          Max.   :560.000         Max.   :149.400        
    ##  Data.Vitamins.Vitamin.K
    ##  Min.   :   0.00        
    ##  1st Qu.:   0.80        
    ##  Median :   3.80        
    ##  Mean   :  14.21        
    ##  3rd Qu.:   9.30        
    ##  Max.   :1640.00

# Очистка данных

1)  Уберите переменные, в которых пропущенных значений больше 20% или
    уберите субъектов со слишком большим количеством пропущенных
    значений. Или совместите оба варианта. Напишите обоснование, почему
    вы выбрали тот или иной вариант.

Сначала посмотрим, сколько пропущенных значений есть в нашей таблице:

``` r
sum(is.na(food))
```

    ## [1] 0

**Обоснование**: Мы видим, что их нет, значит дополнительно
преобразовывать таблицу не нужно (иногда пропущенные значения
неправильно отображаются, если, например, их обозначают знаком “-” или
0. Однако в этих данных все переменные, которые должны быть численными,
считываются корректно, значит в клетках не встречается нечисленных
символов. И значение 0 является обычным измерением, ведь в каких-то
продуктах могут отсутсвовать определенные элементы).

Но если бы в данных были пропущенные значения, я бы могла выбрать разные
тактики работы с ними в зависимости от поставленной задачи и паттерна их
распределения по столбцам и строкам (если нам хватает измерений, то
лучше удалить строки, чем потерять целый фактор для анализа, но если
измерений немного и большая часть пропущенных значений в одном столбце,
то лучше удалить этот столбец и иметь возможность изучить все остальные
переменные на достаточной количестве строк)

2)  Переименуйте переменные в человекочитаемый вид (что делать с
    пробелами в названиях?);

3)  В соответствии с описанием данных приведите переменные к нужному
    типу (numeric или factor);

4)  Отсортируйте данные по углеводам по убыванию;

5)  Сохраните в файл outliers.csv субъектов, которые являются выбросами
    (например, по правилу трёх сигм) — это необязательное задание со
    звёздочкой;

6)  Отфильтруйте датасет так, чтобы остались только Rice и Cookie
    (переменная Category и есть группирующая);

7)  Присвойте получившийся датасет переменной “cleaned_data”.

``` r
cleaned_data <- food %>% 
  mutate(across(c(Category, Description, Nutrient.Data.Bank.Number), ~ as.factor(.x))) %>% 
  rename_with(function(x) x %>% stri_replace_all_regex(c("Data.", "Fat.", "Vitamins.", "Major.Minerals.", "\\."), c("", "", "", "", " "), vectorize_all = FALSE)) %>%
  rename('Nutrient Data Bank Number' = 'Nutrient Bank Number')%>%
  arrange(desc(Carbohydrate)) %>%
  filter(Category %in% c("Rice", "Cookie"))
```

# Сколько осталось переменных?

``` r
ncol(cleaned_data)
```

    ## [1] 38

# Сколько осталось случаев?

``` r
nrow(cleaned_data)
```

    ## [1] 243

# Есть ли в данных идентичные строки?

``` r
nrow(cleaned_data) - nrow(distinct(cleaned_data))
```

    ## [1] 0

Нет

# Сколько всего переменных с пропущенными значениями в данных и сколько пропущенных точек в каждой такой переменной?

``` r
cleaned_data %>% 
  mutate(across(where(is.numeric), ~ as.character(.x))) %>% 
  pivot_longer(colnames(cleaned_data), names_to = "Variable")%>%
  group_by(Variable)%>%
  summarise('Number of NA'= sum(is.na(value)))%>%
  filter(`Number of NA` != 0)
```

    ## # A tibble: 0 x 2
    ## # i 2 variables: Variable <chr>, Number of NA <int>

Приведенный код вывел бы переменные с пропущенными значениями, а также
количество этих значений, однако в таблице они отсутсвуют.

# Описательные статистики

## Количественные переменные

1)  Рассчитайте для всех количественных переменных для каждой группы
    (Category):

1.1) Количество значений;

1.2) Количество пропущенных значений;

1.3) Среднее;

1.4) Медиану;

1.5) Стандартное отклонение;

1.6) 25% квантиль и 75% квантиль;

1.7) Интерквартильный размах;

1.8) Минимум;

1.9) Максимум;

1.10) 95% ДИ для среднего - задание со звёздочкой.

``` r
numeric_stat_table <- cleaned_data %>% 
  pivot_longer(!c(Category, Description, 'Nutrient Data Bank Number'), names_to = 'Variable')%>%
  group_by(Category,Variable)%>%
  summarise('Number of values'= n(),
            'Number of NA' = sum(is.na(value)),
            Mean = mean(value),
            Median = median(value),
            'Standart Deviation' = sd(value),
            Q25 = quantile(value, 0.25),
            Q75 = quantile(value, 0.75),
            IQR = quantile(value, 0.75)- quantile(value, 0.25),
            Min = min(value),
            Max = max(value))

numeric_stat_table %>% head()
```

    ## # A tibble: 6 x 12
    ## # Groups:   Category [1]
    ##   Category Variable           `Number of values` `Number of NA`  Mean Median
    ##   <fct>    <chr>                           <int>          <int> <dbl>  <dbl>
    ## 1 Cookie   Alpha Carotene                    100              0  8.25    0  
    ## 2 Cookie   Beta Carotene                     100              0 17.4     0  
    ## 3 Cookie   Beta Cryptoxanthin                100              0  0.38    0  
    ## 4 Cookie   Calcium                           100              0 33.2    28  
    ## 5 Cookie   Carbohydrate                      100              0 68.1    67.8
    ## 6 Cookie   Cholesterol                       100              0  8.68    0  
    ## # i 6 more variables: `Standart Deviation` <dbl>, Q25 <dbl>, Q75 <dbl>,
    ## #   IQR <dbl>, Min <dbl>, Max <dbl>

## Категориальные переменные

1)  Рассчитайте для всех категориальных переменных для каждой группы
    (Category):

1.1) Абсолютное количество;

1.2) Относительное количество внутри группы;

1.3) 95% ДИ для доли внутри группы - задание со звёздочкой.

``` r
factor_stat_table <- cleaned_data %>% 
  select(c(Category, Description))%>%
  count(Category, Description)%>%
  group_by(Category)%>%
  mutate('Percentage of сategory' = str_c(round(n/sum(n)*100, 2), "%"))%>%
  rename('Number of cases' = n) 

factor_stat_table
```

    ## # A tibble: 243 x 4
    ## # Groups:   Category [2]
    ##    Category Description                 `Number of cases` Percentage of сatego~1
    ##    <fct>    <fct>                                   <int> <chr>                 
    ##  1 Cookie   Cookie, almond                              1 1%                    
    ##  2 Cookie   Cookie, animal                              1 1%                    
    ##  3 Cookie   Cookie, animal, with frost~                 1 1%                    
    ##  4 Cookie   Cookie, applesauce                          1 1%                    
    ##  5 Cookie   Cookie, baby food                           1 1%                    
    ##  6 Cookie   Cookie, bar, with chocolate                 1 1%                    
    ##  7 Cookie   Cookie, batter or dough, r~                 1 1%                    
    ##  8 Cookie   Cookie, biscotti                            1 1%                    
    ##  9 Cookie   Cookie, brownie, fat free,~                 1 1%                    
    ## 10 Cookie   Cookie, brownie, NS as to ~                 1 1%                    
    ## # i 233 more rows
    ## # i abbreviated name: 1: `Percentage of сategory`

# Визуализация

## Количественные переменные

1)  Для каждой количественной переменной сделайте боксплоты по группам.
    Расположите их либо на отдельных рисунках, либо на одном, но
    читаемо;

2)  Наложите на боксплоты beeplots - задание со звёздочкой.

3)  Раскрасьте боксплоты с помощью библиотеки RColorBrewer.

Можно построить все боксплоты сразу при помощи facet_wrap, но в таком
случае на всех графиках будут одинаковые пределы осей. К сожалению,
переменные в данном датасете сильно отличаются друг от друга, поэтому
сравнение их друг с другом затруднительно:

``` r
cleaned_data %>% 
  select(Category, where(is.numeric))%>% 
  pivot_longer(!Category)%>%
  ggplot(aes(y = value, x = Category, fill = Category))+
  geom_boxplot()+

  theme_bw()+
  theme(
    axis.text.x = element_text(size = 10)
  )+
  labs(x = "",
       y = "")+
  facet_wrap(~name)+
  scale_fill_manual(values = brewer.pal(2, "Set1"))
```

![](homework_notebook_02_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

Можно построить аналогичные графики для каждой переменной независимо, в
таком случае переменные будет трудно сравнивать друг с другом, зато
боксплоты будут в большинстве своем информативны

``` r
x <- cleaned_data %>% 
  select(where(is.numeric))%>%
  colnames()

list_of_plots <- list()

for (i in x){
  plot <- cleaned_data %>% 
  select(Category, i)%>% 
  pivot_longer(!Category)%>%
  ggplot(aes(y = value, x = Category, fill = Category))+
  geom_boxplot(outliers = FALSE)+
  geom_quasirandom(color = "lightgray", shape = 1)+
  theme_bw()+
  theme(
    axis.text.x = element_text(size = 10),
    legend.position = "None"
  )+
  labs(x = "",
       y = "")+
  facet_grid(~name)+
  scale_fill_manual(values = brewer.pal(2, "Set1"))
  
  list_of_plots = c(list_of_plots, list(plot))
}

ggarrange(plotlist = list_of_plots,
          nrow = 5,
          ncol = 7)
```

![](homework_notebook_02_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

## Категориальные переменные

1)  Сделайте подходящие визуализации категориальных переменных.
    Обоснуйте, почему выбрали именно этот тип.

Единственная категориальная переменная, которую имеет смысл
визуализировать - это категория продукта (их всего две). Можно показать
количество записей в каждой из двух категорий с помощью столбиковой
диаграммы или долю записей в каждой атегории от общего количества.

``` r
cleaned_data %>% 
  ggplot(aes(x = Category, fill = Category))+
  geom_bar()+
  theme_bw()+
  theme(legend.position = "None")+
  labs(x = "")+
  scale_fill_manual(values = brewer.pal(2, "Set1"))
```

![](homework_notebook_02_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

# Статистические оценки

## Проверка на нормальность

1)  Оцените каждую переменную на соответствие нормальному распределению
    с помощью теста Шапиро-Уилка. Какие из переменных являются
    нормальными и как как вы это поняли?

``` r
cleaned_data %>% 
  pivot_longer(!c(Category, Description, 'Nutrient Data Bank Number'), names_to = "Nutrient")%>%
  group_by(Nutrient)%>%
  summarise('p value' = shapiro.test(value)$p.value*35)%>%
  arrange(desc(`p value`))
```

    ## # A tibble: 35 x 2
    ##    Nutrient          `p value`
    ##    <chr>                 <dbl>
    ##  1 Sodium             2.39e- 6
    ##  2 Zinc               5.51e- 9
    ##  3 Phosphorus         2.10e- 9
    ##  4 Magnesium          8.36e-12
    ##  5 Protein            1.16e-13
    ##  6 Potassium          8.57e-14
    ##  7 Total Lipid        1.57e-14
    ##  8 Monosaturated Fat  1.03e-15
    ##  9 Carbohydrate       2.88e-16
    ## 10 Polysaturated Fat  8.33e-17
    ## # i 25 more rows

Тест Шапиро-Уилка проверяет нулевую гипотезу о нормальности
распределения. Если p-value меньше 0.05, но эту гипотезу необходимо
отвергнуть и считать распределение не нормальным. В данном случе даже с
поправкой на множественное тестирование гипотеза о нормальности
отклоняется во всех случаях (наибольшее значение меньше 5%).

2)  Постройте для каждой количественной переменной QQ-плот. Отличаются
    ли выводы от теста Шапиро-Уилка? Какой метод вы бы предпочли и
    почему?

Выводы не отличаются, я бы предпочла тест Шапиро-Уилка, так как QQ-плот
оценивается визуально, из-за чего не является точным методом, особенно
если нужно проверять нормальность 35 переменных за раз (но можно
использовать его как первичный метод анализа, результаты которого будут
дополнительно подтверждены тестом Шапиро-Уилка).

``` r
x <- cleaned_data %>% 
  select(where(is.numeric))%>%
  colnames()

list_of_plots <- list()

for (i in x){
  plot <- cleaned_data %>% 
  select(Category, i)%>% 
  pivot_longer(!Category)%>%
  ggplot(aes(sample = value))+
  facet_grid(~name)+
  stat_qq() + 
  stat_qq_line()+
  theme_bw() 
  
  
  list_of_plots = c(list_of_plots, list(plot))
}

ggarrange(plotlist = list_of_plots,
          nrow = 5,
          ncol = 7)
```

![](homework_notebook_02_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

3)  Ниже напишите, какие ещё методы проверки на нормальность вы знаете и
    какие у них есть ограничения.

**Напишите текст здесь** Критерий Колмогорова-Смирного: применяется для
больших размеров выборок (\>50)

## Сравнение групп

1)  Сравните группы (переменная **Category**) по каждой переменной (как
    количественной, так и категориальной). Для каждой переменной
    выберите нужный критерий и кратко обоснуйте его выбор в
    комментариях.

В данном датасете помимо переменной **Category** есть описание
(Description) и номер в банке (Nutrient Data Bank Number), которые
являются уникальными для каждой записи. Сравнивать их между двумя
группами не представляется возможным (и осмысленным). Единственная
категориальная переменная - это сама **Category**, сравнить ее можно
лишь по количеству записей в каждой из двух групп, что уже было сделано
ранее. Остается еще 35 количественных переменных, отражающих содержание
различных ингридиентов и микроэлементов в рисе и печенье. Можно для
каждого ингридиента проверить, различается ли его среднее содержание в
этих двух продуктах или нет. Мы уже поняли, что данные имеют
ненормальное распределение, поэтому использовать можно только
непараметрические тесты, например, тест Манна-Уитни. При этом нужно не
забыть поправку на множественное тестирование. Почти для всех
ингридиентов можно отвертгуть нулевую гипотезу о равенстве средних

``` r
cleaned_data %>% 
  pivot_longer(!c(Category, Description, 'Nutrient Data Bank Number'), names_to = "Nutrient")%>%
  group_by(Nutrient)%>%
  summarise('p value adjusted' = wilcox.test(value ~ Category)$p.value*35)%>%
  arrange(desc(`p value adjusted`))
```

    ## # A tibble: 35 x 2
    ##    Nutrient              `p value adjusted`
    ##    <chr>                              <dbl>
    ##  1 Cholesterol                   11.1      
    ##  2 Beta Cryptoxanthin             8.44     
    ##  3 Zinc                           2.97     
    ##  4 Vitamin K                      0.0197   
    ##  5 Retinol                        0.0109   
    ##  6 Lutein and Zeaxanthin          0.00111  
    ##  7 Calcium                        0.000409 
    ##  8 Magnesium                      0.000204 
    ##  9 Lycopene                       0.000136 
    ## 10 Choline                        0.0000461
    ## # i 25 more rows

``` r
 # flextable::flextable()
```

Гипотеза не отвергается всего для трех ингридиентов:

``` r
cleaned_data %>% 
  select(Category, Cholesterol, `Beta Cryptoxanthin`, Zinc)%>% 
  pivot_longer(!Category)%>%
  ggplot(aes(y = value, x = Category, fill = Category))+
  geom_boxplot(outliers = FALSE)+
  theme_bw()+
  theme(
    axis.text.x = element_text(size = 10),
    legend.position = "None"
  )+
  labs(x = "",
       y = "")+
  facet_grid(~name)+
  scale_fill_manual(values = brewer.pal(2, "Set1"))
```

![](homework_notebook_02_files/figure-gfm/unnamed-chunk-18-1.png)<!-- -->

# Далее идут **необязательные** дополнительные задания, которые могут принести вам дополнительные баллы в том числе в случае ошибок в предыдущих

## Корреляционный анализ

1)  Создайте корреляционную матрицу с визуализацией и поправкой на
    множественные сравнения. Объясните, когда лучше использовать
    корреляционные матрицы и в чём минусы и плюсы корреляционных
    исследований.

## Моделирование

1)  Постройте регрессионную модель для переменной **Category**. Опишите
    процесс построения
