Lab 02 - Plastic waste
================
Lily-Mai Blais
15-09-2025

## Chargement des packages et des données

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read_csv("data/plastic-waste.csv")

ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap)) +
  geom_histogram(binwidth = 0.2)
```

    ## Warning: Removed 51 rows containing non-finite outside the scale range
    ## (`stat_bin()`).

![](lab-02_files/figure-gfm/load-data-1.png)<!-- -->

``` r
plastic_waste %>%
  filter(plastic_waste_per_cap > 3.5)
```

    ## # A tibble: 1 × 10
    ##   code  entity              continent     year gdp_per_cap plastic_waste_per_cap
    ##   <chr> <chr>               <chr>        <dbl>       <dbl>                 <dbl>
    ## 1 TTO   Trinidad and Tobago North Ameri…  2010      31261.                   3.6
    ## # ℹ 4 more variables: mismanaged_plastic_waste_per_cap <dbl>,
    ## #   mismanaged_plastic_waste <dbl>, coastal_pop <dbl>, total_pop <dbl>

Commençons par filtrer les données pour retirer le point représenté par
Trinité et Tobago (TTO) qui est un outlier.

``` r
plastic_waste <- plastic_waste %>%
  filter(plastic_waste_per_cap < 3.5)
```

## Exercices

### Exercise 1

``` r
ggplot(plastic_waste, aes(x = plastic_waste_per_cap )) +
  geom_histogram(binwidth = 0.25) +
  facet_wrap(~ continent) +
  labs(title = "Distribution de la quatité de déchets plastiques par habitant classée par continent",
       x = "Quantité de déchets plastiques par habitant (kg/pers)",
       y = "Nombre de pays") 
```

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- --> Avec
la distribution suivante, on peut observer que la majorité des pays
d’Asie, d’Europe, d’Amérique du Sud et d’Amérique du Nord semblent une
quantité de déchets par habitant qui tourne autour de 0,25 kg/pers. On
voit qu’en Afrique, la majorité des pays ont une quantité de déchets
plastiques qui se retrouvent proche de 0,00 kg/pers.

### Exercise 2

``` r
ggplot(plastic_waste, aes(x = plastic_waste_per_cap,
                          color = continent,
                          fill = continent)) + 
  geom_density(adjust = 2,
               alpha = 0.4) + 
  labs(title = "Quantité de déchets plastiques selon la densité par continent",
       x = "Quantité de déchets plastiques par habitant (kg/pers)",
       y = "Densité par continent",
       color = "Continent",
       fill = "Continent")
```

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->

Réponse à la question…

Le réglage de la couleur (color et fill) ne sont pas au même endroit que
la transparence (alpha) parce qu’on assigne directement sur les
variables du jeu de donnée la couleur tandis que la transparence est
associée au graphique lui-même et non à une variable en particulier. On
ne peut pas vraiment mettre une variable plus transparente ou moins
transparente. On peut lui assigner toutefois une couleur.

### Exercise 3

Boxplot:

``` r
ggplot(plastic_waste, aes(x = continent,
                          y = plastic_waste_per_cap)) + 
  geom_boxplot()
```

![](lab-02_files/figure-gfm/plastic-waste-boxplot-1.png)<!-- -->

Violin plot:

``` r
ggplot(plastic_waste, aes(x = continent,
                          y = plastic_waste_per_cap)) +
  geom_violin()
```

![](lab-02_files/figure-gfm/plastic-waste-violin-1.png)<!-- -->

Réponse à la question…

Les violin plots nous permettent de voir où se situe le plus de pays par
rapport à la quantité de déchets plastique par habitant selon chaque
continent et comment le nombre de pays est réparti selon la quantité de
déchets plastiques par habitant qui augmente. On voit une sorte de
progression que le boxplot ne nous permet pas de voir. Avec ce dernier,
on peut seulement de voir où se trouve en moyenne les pays et
l’intervalle auquel ils se situent.

### Exercise 4

``` r
# insert code here
```

Réponse à la question…

### Exercise 5

``` r
# insert code here
```

``` r
# insert code here
```

Réponse à la question…

## Conclusion

Recréez la visualisation:

``` r
# insert code here
```
