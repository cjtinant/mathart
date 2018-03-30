# Math art

Create mathematical art with R

## How to use

### Install the packages

```R
install.packages(c("devtools", "mapproj", "tidyverse", "ggforce"))
devtools::install_github("marcusvolz/mathart")
devtools::install_github("marcusvolz/ggart")
```

### Load the libraries

```R
library(mathart)
library(ggart)
library(ggforce)
library(tidyverse)
```

### Create birds

```R
df <- rbind(parrot() %>% mutate(id = 1),
            stork() %>% mutate(id = 2),
            magpie() %>% mutate(id = 3))

p <- ggplot() +
  geom_point(aes(x, y, alpha = r), df, size = 0.03) +
  facet_wrap(~id, nrow = 2, scales = "free") +
  scale_alpha_continuous(range = c(0.03, 0.06)) +
  theme_blankcanvas(margin_cm = 1)

ggsave("birds01.png", p, width = 20, height = 20, units = "cm", dpi = 300)
```

![birds](https://github.com/marcusvolz/mathart/blob/master/plots/birds01.png "Birds")
### Create plants

```R
df <- rbind(olive_branch() %>% mutate(id = 1),
            palm_branch() %>% mutate(id = 2),
            branch() %>% mutate(id = 3))

p <- ggplot() +
  geom_circle(aes(x0 = x, y0 = y, r = r), df, size = 0.03, alpha = 0.1) +
  coord_equal() +
  facet_wrap(~id, nrow = 3) +
  theme_blankcanvas(margin_cm = 1)

ggsave("plants01.png", p, width = 20, height = 20, units = "cm")
```

![plants](https://github.com/marcusvolz/mathart/blob/master/plots/plants01.png "Plants")

### Create mollusc shells

```R
df <- mollusc()
df1 <- df %>% mutate(id = 1)
df2 <- df %>% mutate(id = 2)
df3 <- df %>% mutate(id = 3)

p <- ggplot() +
  geom_point(aes(x, y), df1, size = 0.03, alpha = 0.03) +
  geom_path( aes(x, y), df1, size = 0.03, alpha = 0.03) +
  geom_point(aes(x, z), df2, size = 0.03, alpha = 0.03) +
  geom_path( aes(x, z), df2, size = 0.03, alpha = 0.03) +
  geom_point(aes(y, z), df3, size = 0.03, alpha = 0.03) +
  geom_path( aes(y, z), df3, size = 0.03, alpha = 0.03) +
  facet_wrap(~id, nrow = 2, scales = "free") +
  theme_blankcanvas(margin_cm = 0.5)

ggsave("mollusc01.png", width = 20, height = 20, units = "cm")
```

![plants](https://github.com/marcusvolz/mathart/blob/master/plots/mollusc01.png "Mollusc shells")
