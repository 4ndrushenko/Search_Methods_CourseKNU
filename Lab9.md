Lab9.R
================
``` r
## Зчитування html сторінки
library("rvest")
htmlpage <- read_html("http://www.imdb.com/search/title?count=100&release_date=2019,2019&title_type=feature")
html <- html_nodes(htmlpage,'.text-primary')
rank <- as.numeric(html_text(html))
title_html <- html_nodes(htmlpage,'.lister-item-header a')
title <- html_text(title_html)
runtime_html <- html_nodes(htmlpage,'.text-muted .runtime')
runtime <- html_text(runtime_html)
runtime <- as.numeric(gsub(" min", "", runtime))
movies <- data.frame(Rank = rank, Title = title, Runtime = runtime, stringsAsFactors = FALSE )

## 1.   Виведіть перші 6 назв фільмів дата фрейму.

head(movies$Title)
```

    ## [1] "Джентльмени"         "Ножі наголо"         "Джокер"             
    ## [4] "Месники: Завершення" "Термінатор: Фатум"   "Паразити"

``` r
## 2.   Виведіть всі назви фільмів с тривалістю більше 120 хв.

movies[movies$Runtime > 120, ]$Title
```

    ##  [1] "Ножі наголо"                                  
    ##  [2] "Джокер"                                       
    ##  [3] "Месники: Завершення"                          
    ##  [4] "Термінатор: Фатум"                            
    ##  [5] "Паразити"                                     
    ##  [6] "Одного разу... в Голлівуді"                   
    ##  [7] "Аутсайдери"                                   
    ##  [8] "Доктор Сон"                                   
    ##  [9] "Сонцестояння"                                 
    ## [10] "Зоряні війни: Епізод 9 - Скайвокер. Сходження"
    ## [11] "Маленькі жінки"                               
    ## [12] "Dolly Kitty Aur Woh Chamakte Sitare"          
    ## [13] "Sound of Metal"                               
    ## [14] "Джуманджі: Наступний рівень"                  
    ## [15] "Мідвей"                                       
    ## [16] "Неограновані коштовності"                     
    ## [17] "Король"                                       
    ## [18] "Ірландець"                                    
    ## [19] "Людина-павук: Далеко від дому"                
    ## [20] "Капітан Марвел"                               
    ## [21] "Воно 2"                                       
    ## [22] "Аладдін"                                      
    ## [23] "Річард Джуелл"                                
    ## [24] "Аліта: Бойовий ангел"                         
    ## [25] "Портрет дівчини у вогні"                      
    ## [26] "6 футів під землею"                           
    ## [27] "До зірок"                                     
    ## [28] "Рокетмен"                                     
    ## [29] "Шлюбна історія"                               
    ## [30] "Форсаж: Гоббс та Шоу"                         
    ## [31] "Джон Вік 3"                                   
    ## [32] "Сирота Бруклін"                               
    ## [33] "Шазам!"                                       
    ## [34] "Темні води"                                   
    ## [35] "Ґодзілла II: Король Монстрів"                 
    ## [36] "Скло"                                         
    ## [37] "El Camino: A Breaking Bad Movie"              
    ## [38] "Падіння янгола"                               
    ## [39] "Приховане життя"                              
    ## [40] "Пригоди Піноккіо"                             
    ## [41] "Квін та Слім"                                 
    ## [42] "Абатство Даунтон"                             
    ## [43] "Щиголь"

``` r
## 3.   Скільки фільмів мають тривалість менше 100 хв.

length(which(movies$Runtime < 100))
```

    ## [1] 22
