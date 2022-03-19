# Gym meme

### Why make this meme?

As a part of my assignment, I had to make an original meme using Rstudio. I've invested myself into going to the gym for the past few months and thought that an appropriate meme idea would be one of the struggles about going to the gym. The meme uses two images from an already very popular meme format of a man's happy but then dissapointed expression. Pre-workout helps so much in making a gym session enjoyable and more productive, but forgetting it when the gym is quiet (which is rare) is soul-crushing. 

##
![Gym_meme](https://user-images.githubusercontent.com/100755107/159112621-9deb4969-a96d-4b66-b7fc-9088b30d8207.png) 
##

### How did I make this?

To make this meme I used Rstudio along with the {magick} package. Below you can find the code I used to produce the meme and the steps taken to do so.

```r
happy_face <- image_read("https://64.media.tumblr.com/7903b23fc36d7f23ab5408115f0af227/77e3be074fab1668-3d/s500x750/908430bf379b3ef61bbdb5b5e5d3c65d3a836c56.jpg") %>% image_scale(400)

sad_face <- image_read("https://www.meme-arsenal.com/memes/d3756629b9bbeaa6018f4fedfcaaa7eb.jpg") %>% image_scale(400)

happy_text <- image_blank(height = 400,
                          width = 400,
                          color = "#ffffff") %>% image_annotate(text = "Getting to the gym and all\nthe machines are free",
                                                                color = "#000000",
                                                                size = 30,
                                                                font = "Impact",
                                                                gravity = "center")

sad_text <- image_blank(height = 400,
                        width = 400,
                        color ="#ffffff") %>% image_annotate(text = "You left your pre-workout\nat home",
                                                             color = "#000000",
                                                             size = 30,
                                                             font = "Impact",
                                                             gravity = "center")

first_row <- c(happy_text, happy_face) %>% image_append()

second_row <- c(sad_text, sad_face) %>% image_append()

meme <- c(first_row, second_row) %>% 
                         image_append(stack = TRUE)

image_write(meme, "Gym_meme.png")
```
