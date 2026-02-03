# Kamilar and Cooper 2013 data


f <- "https://github.com/difiore/ada-datasets/blob/main/KamilarAndCooperData.csv"

v <- file.choose()

d <- read_csv(file = v, col_names=TRUE)

attach(d)
mean(Brain_Size_Female_Mean, na.rm = TRUE)
detach(d)
mean(Brain_Size_Female_Mean, na.rm = TRUE) # throws an error

with(d, mean(Brain_Size_Female_Mean, na.rm = TRUE))

summary(d)     


library(skimr)
head(skim(d))
tail(skim(d))

boxplot(log(d$Body_mass_female_mean))
stripchart(log(d$Body_mass_female_mean))
stripchart(log(d$Body_mass_female_mean), method= "overplot", col="blue", vertical = TRUE, add = TRUE)
boxplot(data = d, log(d$Body_mass_female_mean))
stripchart(log(d$Body_mass_female_mean), method = "jitter", col= "blue", vertical = TRUE, add = TRUE)

?stripchart

boxplot(data = d, log(d$Body_mass_female_mean) ~ Family)
stripchart(log(d$Body_mass_female_mean) ~ d$Family, method = "jitter", col = "blue", vertical= TRUE, add = TRUE)


boxplot(data = d, log(d$Body_mass_male_mean) ~ Family)
stripchart(log(d$Body_mass_male_mean) ~ d$Family, method = "jitter", col = "blue", vertical= TRUE, add = TRUE)


p <- ggplot(data= d, aes(x = Family, y = log(d$Body_mass_female_mean))) + geom_boxplot(na.rm = TRUE)

p

p <- p + geom_jitter(color = "blue", width = 0.1) 
  
p 


hist(log(d$Body_mass_female_mean))
hist(log(d$Body_mass_female_mean), freq = TRUE), col = "blue")


p <- ggplot(data= d, aes(x = Family, y = log(d$Body_mass_female_mean)))
p
(p + geom_histogram(bins=9,  aes (y = ..density..))
(p + geom_histogram(bins=9, aes (y = ..density..))+geom_density())


plot(x=log(d$Body_mass_female_mean))

p <- p + geom_point(aes(color = factor(family)), na.rm = (TRUE)
p
