---
title: "JedR Trial: Intro"
engine: knitr
format: live-html
webr:
  packages:
    - tidyverse
    - dplyr
    
  # render-df: paged-table
live:
  show-hints: true
---

{{< include ./_extensions/r-wasm/live/_knitr.qmd >}}


```{webr}
#| include: FALSE
praise_list <- c("Great job you have done!", "Nice work. You have controlled your fear.", "Wow! The force is with you!", "Great job! Mind tricks don't work on you!", "The Force is strong with you!", "You’ve mastered this task like a true Jedi Knight.", "Your skills rival those of a seasoned Jedi Master.", "The galaxy is lucky to have someone as strong and brave as you.", "The Rebellion couldn’t ask for a better ally.", "You’re the hope the galaxy needs!", "Not even the Death Star could stand in your way.", "Darth Vader would tremble in your presence!", "Even a bounty hunter would be impressed by your precision and focus.", "You’ve got the strength of a thousand stormtroopers (but with way better aim)!", "Like a true Jedi, you face challenges with courage and wisdom.")

random_praise <- sample(praise_list, 1)

again_list <- c("Even Yoda didn’t get it on the first try. Keep going, young Padawan!", "The Force is strong with you—just focus and try again.", "Every Jedi stumbles before mastering the lightsaber. Give it another go!", "Remember, the greatest pilots still had to learn to fly first.", "Even Han Solo missed a few shots—try again, and you’ll hit the mark.", "No need to go to the Dark Side; persistence will bring you victory!", "The path of the Jedi is filled with lessons. This is just one of them.", "Even Anakin faced failure; it’s how you rise that matters.", "Not even a Sith Lord could conquer every challenge the first time.", "Mistakes are like hyperspace jumps: each one gets you closer to the destination.", "The Rebellion wasn’t won in a day — keep fighting for what’s possible.","Think of this as training with Master Yoda: patience leads to mastery.", "The Force is with you, always, so don’t give up now!", "Just like rebuilding a lightsaber, try again, and you'll get it right.")

random_again <- sample(again_list, 1)
```

## JedR Trial No. 1: Introduction

Congratulations! You have recently been hired as a **data jedi** for the *Galactic News Hub*, the premiere news organization for the Star Wars Universe. Your first task: apply beginning `tidyverse` skills to learn about the characters in the Star Wars universe you'll be reporting on.

### 1. Previewing our data

For this exercise, we will use the data collection called `starwars`. This data comes with the `tidyverse` package. As you can see below, `starwars` contains some information about Star Wars characters, like their name and height.

Let's learn a bit more about the structure of the `starwars` data and how to conquer these JedR Trials.

This is what it looks like when we load the `tidyverse` library and look at the first few lines in the `starwars` data. Each row of the data is a character within the Star Wars franchise:

```{webr}
#| edit: false
#| message: false
library(tidyverse)

starwars |> 
  head()
```

Within the JedR Trails, you can enter and run code right inside this page. Please make sure to only remove the **underscores** to add your answers. Since the tidyverse was loaded above, all the functions you would normally see in RStudio are available. Once you enter the code, click the blue **Run Code** button to see the results.

The first thing you need to learn is how many rows are in the `starwars` data, along with all the columns and datatypes.

What function would you add to the `starwars` data here to *glimpse* the data and find those answers?

:::: {.panel-tabset}

## Exercise

```{webr}
#| exercise: ex_1
#| label: glimpse
_______(starwars)
```

## Hint

::: { .hint exercise="ex_1"}
Check out the `glimpse()` function. You can [learn more here](https://dplyr.tidyverse.org/reference/glimpse.html).
:::

::::

```{webr}
#| exercise: ex_1
#| check: true
if (identical(.result, glimpse(starwars))) {
  list(correct = TRUE, message = sample(praise_list, 1))
} else {
  list(correct = FALSE, message = sample(again_list, 1))
}
```

::: {.callout-tip collapse="true"}
## "So, how many characters are there in your data? You might be surprised to see..."

There are **87** characters in the `starwars` dataset!
:::

### 2. Focusing on variables

Now that we know how to *glimpse* into our data, let's work on *select*ing specific variables of interest. Let's say the *Galactic News Hub* has asked you to write a story about height differences across different species. What function would you use to *select* only the following variables in `starwars`: `name`, `height`, `homeworld`, and `species`? (Hint: Write your function in that order!)

```{webr}
#| exercise: ex_3
#| label: selecting
starwars |> 
  ______(____, ______, _________, _______)
```

```{webr}
#| exercise: ex_3
#| check: true

if (identical(.result, starwars |> select(name, height, homeworld, species))) {
  list(correct = TRUE, message = sample(praise_list, 1))
} else {
  list(correct = FALSE, message = sample(again_list, 1))
}
```

::: {.hint exercise="ex_3"}
::: {.callout-note collapse="false"}
## Hint 1

You might look into the `select()` function, you can [learn about here](https://dplyr.tidyverse.org/reference/select.html).

:::
:::

### 3. Arranging our Data

Now that we have *glimpse*d our data and *select*ed our variables in the `starwars`, let's *arrange* them using by height. What function would we add to our code below to *arrange* our data so that the tallest person is listed at the top? (Hint: since `tidyverse` *arrange*s numbers from the smallest to the greatest number, you may need another function so the information is in *desc*ending order.)

```{webr}
#| exercise: ex_4
starwars |>
  ______(____, ______, _________, _______) |>   
  _______(______ |> ____())
```

```{webr}
#| exercise: ex_4
#| check: true

if (identical(.result, starwars |>
  select(name, height, homeworld,species) |>
  arrange(height |> desc()))) {
  list(correct = TRUE, message = sample(praise_list, 1))
} else {
  list(correct = FALSE, message = sample(again_list, 1))
}
```

::: {.hint exercise="ex_4"}
::: {.callout-note collapse="false"}
## Hint 1

I recommend checking out the `arrange()` function, you can [learn about here](https://dplyr.tidyverse.org/reference/arrange.html). Don't forget to put your result in **desc**ending order.

:::
:::

::: {.callout-tip collapse="true"}
## "If J-327D asked you to write about the tallest being in the galaxy, who would it be? Perhaps a towering Wookiee or a menacing Sith lord... Let’s see!"

The tallest character is **Yarael Poof** with a height of **264 cm**.
:::

Great job! Please inform your JedR Master that you have completed this exercise. You have conquered much, but the next trial calls to you through the Force. Do you dare step forward? [Continue Your Journey](/trials/jedr-trial-02-count.html)