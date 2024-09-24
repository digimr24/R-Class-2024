#creates the data frame by reading the csv file
df.t1 <- read.csv("C:/Users/madid/OneDrive/Documents/Desktop/RCourseExamples/R-Class-2024/WK03_Reproducibility/data/tempExperiment-raw.csv")

#separate temperature treatment from population using strsplit
#the unlist and matrix functions rearrange the output of strsplit
a <- strsplit(as.character(df.t1$temp), split = '-') #as.character indicates that it is a character
newvar <- matrix(unlist(a), ncol =2, byrow = TRUE) # takes apart the temp and population and creates a matrix of two colums
head(newvar)# view the new table created


#creating new data frame
df.t2 <- df.t1
df.t2$temp <- newvar[,1] #assigns column 1 of the newvar matrix to the temp column on the new data frame
df.t2$pop <- newvar[,2]# assigns column 2 of the newvar matrix to a new population column

head(df.t2) #view new df

#now I have the correct columns that I want, but within those columns the formats differ
#in temp it is numeric (10) or the word ten, pop is pop or population, need to make both uniform
#they are different levels

df.t2$temp <- sub('ten', '10', df.t2$temp)
df.t2$temp <- sub('twenty', '20', df.t2$temp)
df.t2$pop <- sub('population', 'pop', df.t2$pop)
df.t2$pop <- sub('pop 1','pop1', df.t2$pop)
df.t2$pop <- sub('pop2','pop 2', df.t2$pop)
df.t2$pop <- sub('population 1','pop 1', df.t2$pop)
str(df.t2) #look at structure, found temp to be a character and population to be a character
# need to change these to be factors instead of characters 



df.t2$temp <- factor(df.t2$temp) #changes temp to be a factor
df.t2$pop <- factor(df.t2$pop) #changes pop to be a factor
str(df.t2)#looking at new structure to confirm chr changed to factor
write.csv(df.t2, 'data/tempExperiment_V2.csv') # save new df as a csv
