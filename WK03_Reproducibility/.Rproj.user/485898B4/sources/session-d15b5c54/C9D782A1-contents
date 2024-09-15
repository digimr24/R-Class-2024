setwd("C:/Users/madid/OneDrive/Documents/Desktop/RCourseExamples/R-Class-2024/WK03_Reproducibility")
source("src/EditDataframe.R")
#clearing list
rm(list = ls(all= TRUE))
#reads in CSV of edited data frame
df.t <- read.csv("data/tempExperiment_V2.csv")
str(df.t) #investigate structure

#I need to change temperature and population to be factors
df.t$temp <- factor(df.t$temp)
df.t$pop <- factor(df.t$pop)

#how does temp, population, and size affect growth rate?
#visualizing the data

boxplot(df.t$growthRate ~ df.t$temp + df.t$pop) 

#boxplot version 2
boxplot(df.t$growthRate ~ df.t$temp + df.t$pop,
        names = c('10', '20', '10', '20'), #renaming the labels
        at = c(1,2,4,5),
        ylab = 'Growth rate mm/day',
        xlab = '')

#using mtext to add margin text
mtext('Pop 1', side = 1, at =1.5, line =3)
mtext( 'Pop 2', side = 1, at = 4.5, line =3)

pdf('figures/MyBoxplot.pdf', width = 5, height = 5)

boxplot(df.t$growthRate ~ df.t$temp + df.t$pop,
        names = c('10', '20', '10', '20'), #Temperature label
        at = c(1, 2, 4, 5), # space out the boxes according to population
        ylab = 'Growth rate mm/day',
        xlab = ''
)
# Introducing the 'mtext' command to add margin text
mtext('Pop 1', side = 1, at = 1.5, line = 3)
mtext('Pop 2', side = 1, at = 4.5, line = 3)
dev.off()

#ANOVA analysis
m1 <- aov(df.t$growthRate ~ df.t$temp * df.t$pop)
m1.summary <- summary(m1)
m1.summary #view the summary

saveRDS(m1.summary, 'analysis/m1.summary.rds')
