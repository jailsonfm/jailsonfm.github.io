---
layout: post
title: "The five inequalities"
subtitle: "Faces of inequality for sustainability goals."
background: '/img/posts/08.jpg'
---

Inequality and job opportunities are intricately linked. In a world where certain groups have greater access to education, resources, and networks, they are more likely to secure high-quality jobs that offer better pay, benefits, and career advancement prospects. This, in turn, perpetuates economic inequality, creating a vicious cycle that is difficult to break.

One of the main drivers of inequality in job opportunities is education. People with higher levels of education tend to earn more money and have access to more job opportunities than those with less education. However, education is often expensive, and many people from low-income backgrounds cannot afford it. This creates a barrier to entry for certain jobs that require a degree or specialized training.

Another factor that contributes to inequality in job opportunities is discrimination. Certain groups, such as women, people of color, and people with disabilities, face discrimination in the hiring process and on the job, which limits their access to high-quality jobs. This discrimination can take many forms, from overt bias to unconscious bias, and it can be difficult to address.

Furthermore, access to networks and connections can also play a role in job opportunities. People who have strong professional networks or family connections in certain industries are often better positioned to secure high-quality jobs than those who do not. This can create a situation where jobs are not necessarily awarded based on merit, but rather on who you know.

![image info](/img/posts/image_test.jpg)

To address inequality in job opportunities, a multi-pronged approach is needed. This includes investing in education and job training programs that are accessible to everyone, regardless of their background. It also means addressing discrimination and bias in the hiring process and on the job, and providing support and resources to those who face systemic barriers. Finally, it means creating more opportunities for people from underrepresented groups to build strong professional networks and connections, so that they have equal access to job opportunities. Only by taking a comprehensive approach can we create a more equitable society where everyone has access to the same job opportunities, regardless of their background.

``` r
# LIBRARIES
library(plotly)
library(ggplot2)

set.seed(100) # seed

# LOADING DATA
dia_df <- diamonds[sample(nrow(diamonds), 1000), ]

# PLOTTING with GGPLOT
dia_plot <- ggplot(data = dia_df, aes(x = carat, y = price)) +
        geom_point(aes(text = paste("Clarity:", clarity)), size = 4) +
        geom_smooth(aes(colour = cut, fill = cut)) + facet_wrap(~ cut)

# DYNAMIC PLOTLY PLOTTING STYLE
plly <- ggplotly(dia_plot)

# SAVING THE PLOT AND HTML FILES
htmlwidgets::saveWidget(as_widget(plly), "/Users/jfu/Downloads/Photos-001/pe.html")

# DISPLAY FIGURE IN DYNAMIC FORMAT
<iframe src="/filelocation.html" height="800px" width="100%"></iframe>
```


<iframe src="/img/posts/inequalities/plot_out.html" height="600px" width="100%"></iframe>




``` r
library(plotly)
library(dplyr)
library(gapminder)

data <- gapminder %>% filter(year=="2007") %>% dplyr::select(-year)

# Most basic bubble plot
p <- data %>%
      arrange(desc(pop)) %>%
      mutate(country = factor(country, country)) %>%
      ggplot(aes(x=gdpPercap, y=lifeExp, size=pop, color=continent)) +
        geom_point(alpha=0.5) +
        scale_size(range = c(.1, 24), name="Population (M)")

ggplotly(p)
```

<iframe src="/img/posts/inequalities/plot_gapm.html" height="500px" width="100%"></iframe>
