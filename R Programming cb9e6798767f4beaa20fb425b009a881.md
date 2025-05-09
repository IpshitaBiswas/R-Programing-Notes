# R Programming

# Day 1

To run a program, you need to select the lines to run

# Intro

### Path

To get the current working directory of the environment.

```r
getwd()
```

```r
list.files() #total number of files in the present working directory
length(list.files()) #display the filenames
```

Sets path (for Mac)

```r
setwd("/Users/mac/Desktop/College/R")
```

Sets path (for windows)

```r
setwd("D:\\College\\R course")
```

or

```r
setwd("D:/College/R course")
```

double \ or single /

### Built-in packages

```r
library()
```

![Screenshot 2023-07-24 at 9.42.21 AM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-24_at_9.42.21_AM.png)

To install packages. Eg: XML

Installs from CRAN ( Comprehensive R Archive Network)

```r
install.packages("XML")
```

Shows built-in datasets

```r
data()
```

If we want to use a particular data set .Eg:

```r
data("AirPassengers")
```

We have 2 types of datasets

1. Tabular - on clicking, data shown in tabular format. eg:mtcars
2. Non-tabular - displayed with time series. eg: AirPassengers

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled.png)

- mtcars has a proper data set and format and hence it is shown in tabular form when clicked on
- AirPassesngers doesn’t open when clicked on

### Assignment operators

- operators used for assigning the values

left assign operator←

```r
a<-10
```

right assign operator→

```r
a->10
```

equal to operator= gives error

- variable naming is the same as c language

### Print statement

- for printing a line (string)

```r
print("R programming")
```

- for printing values

```r
a=20
b=10
c=a-b
print(c)
#print("c=", c) #string with variable name does not work, print displays either string or variable
```

- for printing values along with string

```r
a=10
b=10
c=a+b
paste("c=",c)
```

- it can all be done in one line

```r
a=10
b=10
c=a+b
print(paste("c=",c))
```

- Removes the space

```r
paste0("c=", c)
```

- printf from c
prints with %d, %f, etc

```r
sprintf("c=%d",c)
```

- Concatenation of string and value

```r
cat("c=",c)
```

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%201.png)

# Data types

class(x) -displays the data type of the value of x

1. Numeric

```r
x <- 10.5 #decimal value is numeric
class(x)
```

1. Integer

```r
x <- 10L #L represents integer value
class(x)
```

1. Logical / Boolean

```r
x<-TRUE
class(x)
```

1. RAW Data Type

Specifies values as raw bytes

       A given value can be converted into a raw data type

- give a string and convert to raw data type

```r
r=charToRaw("Hello")
class(r)
```

- to convert raw back to character

```r
r=charToRaw("Hello")
#now the char is raw 
r=rawToChar(r)
#now it is char
class(r)
```

### Converting to Integer

```r
as.integer("4") #4
as.integer("1.6") #1
as.integer("-3.2") #-3
as.integer("0x400") #1024
```

### Converting to Character

```r
as.character(1)
as.character(2 + 3)
as.character(1.5)
```

# Reading input

Default: String

- For integer, you have to convert after

```r
readline("Enter your name:")
```

- After execution, user can give input
Without variable name, its not getting stored

```r
a = readline("Enter your name:")
```

- With variable, its stored in environment

For getting multiple inputs use curly braces{}

```r
{
name=readline("Enter your name:")
SRN=readline("Enter your SRN:")
}
```

### Input from text file

- create a text file in the same directory and then use the following code to read from the txt file

```r
readLines("textfile.txt")
#don't forget to add file extension
#L capital 
```

- create a text file in  a different directory and then use the following code to read from the txt file

```r
readLines("path")
```

- can be assigned to a variable

```r
readtext=readLines("textfile.txt")
```

- Copies text from one file and stores it in another
- Also creates a new text file in the same directory

```r
file=readLines("textfile.txt") #stored in variable file
writeLines(file,"textfile2.txt") #Creates a new file Demo2 with text of Demo1
```

### Reading from a CSV file

- To read a csv file

```r
z=read.table("csv.csv")
```

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%202.png)

- to read and differentiate between the rows and columns we add ***separator***

```r
z=read.table("csv.csv", sep=",")
```

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%203.png)

- To make the first row a table header

```r
z=read.table("CSV1.csv", sep = ",", header = TRUE )
```

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%204.png)

- head(z)-first n rows of the dataset is printed
- tail(z)- last n rows of the data set is printed

```r
z=read.table("csv.csv", sep=",", header = TRUE)
head(z)
tail(z)
```

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%205.png)

# Built-in functions

### Math Functions

```r
max(5,10,15)
min(5, 10, 15)
sqrt(16)
abs(-4.7) #4.7
ceiling (1.4)
floor(1.4)
```

### Letters

```r
LETTERS[10] #Only gives 10th letter
LETTERS[1:10] #Prints the letters in range
LETTERS[1:30]
```

### Month

```r
month.name #Gives full name
month.abb #Gives abbreviation
```

### dput() and dget()

```r
x <- data.frame(Name="Mr. A", Gender = "Male", Age = "35")
dput(x)
```

![Screenshot 2023-07-24 at 2.19.54 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-24_at_2.19.54_PM.png)

```r
x <- data.frame(Name="Mr. A", Gender = "Male", Age = "35")
dput(x) 
dput(x,file = "/Users/mac/Desktop/College/R/dput.r") 
y <-dget("/Users/mac/Desktop/College/R/dput.r")
```

- dput() - Stores the dataframe values in a structure/object
dput(path) - Creates the file and stores it
- dget() - Converts a dput file back

### dump()

- dump() - Store data of any data type, in whatever way you’ve given it as

```r
x <- 100
d <- data.frame(Name="Mr. A", Gender = "Male", Age = "35")
dump(c("x","d"),file="/Users/mac/Desktop/College/R/dump.r")
```

### source()

include external code into your current R session.

```r
source("/Users/mac/Desktop/College/R/dump.r")
x
d
str(d)
```

loads an external R script "dump.r," accesses the variables "x" and "d" defined in that script, and then prints information about the structure of the "d" variable.

# Assignment 1

1. Create a dataset. Fetch and display the data.
2. Tell user to give, name, SRN, 3 subject Marks
3. Display and save total marks into a different file

```r
#Part 1: Create a dataset. Fetch and display the data.
forestfire=read.table("forestfires.csv")
forestfire=read.table("forestfires.csv", sep = ",", header = TRUE )

#Part 2: Tell user to give, name, SRN, 3 subject Marks. Display and save total marks into a different file
{  
name=readline("Enter your name:")  
SRN=readline("Enter your SRN:")  
Sub1=readline("Enter Subject 1 marks:")  
Sub2=readline("Enter Subject 2 marks:")  
Sub3=readline("Enter Subject 3 marks:")}

total = as.integer(Sub1)+as.integer(Sub2)+as.integer(Sub3)
l=as.character(total)
writeLines(l,"sum.txt")

x <- data.frame(Name = name, SRN = SRN, Subject1 = Sub1, Subject2 = Sub2, Subject3 = Sub3 )
dput(x,file = "/Users/mac/Desktop/College/R/details.r") 
y <-dget("/Users/mac/Desktop/College/R/details.r")
y
```

# Day 2

# Bind

### Row Bind

```r
df=data.frame(name="PES", age="50")
df
df=data.frame(name=c("a","b","c"), age=c(11,12,13))
df1=data.frame(name=c("d","e"), age=c(11,12))
df3=rbind(df,df1) #Row Bind, common column names(wont be repeated)
df4=cbind(df,df1) #Error, column bind requires same number of rows
```

### Column Bind

```r
df=data.frame(name="PES", age="50")
df
df=data.frame(name=c("a","b","c"), age=c(11,12,13))
df2=data.frame(name=c("f","g","h"), age=c(10,11,12))
df4=cbind(df,df2) #Column Bind
```

### Length

Gives no of columns

```r
length(df)
```

# Operators

### Arithmetic Operators

```r
a <-2
b <-3

print(a+b)
print(a-b)
print(a*b)
print(a/b)
```

```r
a <-2
b <-3
print(a%%b) #Modulus 
print(a%/%b) #Integer division, without decimal value
print(a^b)
```

### Miscellaneous Operators

```r
a1<-8
a2<-12
t <- 1:10 #Colon opperator, gives range
print(a1%in%t) #Checks if its in the list/vector
print(a2%in%t)
```

# Data Structures

## Vectors

c used to create vector

### Print or Remove

```r
a=c(2,3,4,5,6) #c used to create vector
b=c("a","b","c","d")

a[1]
a[c(1,3)] #1st and 3rd value printed
a[c(1:3)] #1st to 3rd value printed

a[c(-1)] #1st element removed
#a[c(-n)] nth element removed
```

### Replace

```r
b=c("a","b","c","d")
b[1]<- "pear"
b
```

### Built-in sorting

```r
a=c(2,3,4,5,6)
sort(a)
```

### Print pattern

```r
a=c(1,2,3)

#1 1 1 2 2 2 3 3 3
r=rep(a)
r=rep(c(1,2,3),each=4)
r

#1 2 3 1 2 3 1 2 3
r=rep(a,3)

#1 1 1 1 2 3 3 
r=rep(c(1,2,3), times=c(4,1,2))
r

#1234234234
r=rep(c(2,3,4),3)
append(r,1,after=0)
```

Append(list,value,poition)

```r
append(r,1,after=0)
```

## List

```r
d <- list("apple","banana","cherry")
d

append(d,"orange") #Appends to the end, does not store it in environment
append(d,"orange", after = 2) #Added at 3rd value
```

## Arrays

### Creating Array

```r
a <- c(1:5)
a
```

### Pattern Printing

To create two dimensional array, 
td=array(data,dim,dimname)

[1] 1 2

```r
a <- c(1:5)
td=array(a, dim = 2)
td
```

[,1] [,2]
[1,] 1 4
[2,] 2 5
[3,] 3 1

```r
a <- c(1:5)
td=array(a, dim = c(3,2))
td
```

## Matrices

### Creating Matrix

1. Column-wise (default)
    
    [,1] [,2] [,3]
    [1,] 1 4 1
    [2,] 2 5 2
    [3,] 3 6 3
    

```r
m=matrix(c(1,2,3,4,5,6),nrow = 3, ncol = 3)
m
```

1. Row-wise
    
    [,1] [,2] [,3]
    [1,] 1 2 3
    [2,] 4 5 6
    [3,] 1 2 3
    

```r
m=matrix(c(1,2,3,4,5,6),nrow = 3, ncol = 3, byrow = TRUE)
m
```

### Display

```r
m=matrix(c(1,2,3,4,5,6),nrow=3,ncol=3,byrow = TRUE)

#to display a particular row
m[2,]
#to display a particular column
m[,2]
#to display a particular number 
m[1,3]
```

byrow can be used only in matrices 

# Conditional Statements

## If

```r
a <- 33
b <- 200
if(b>a){  
	print("b is greater than a")
}
```

### If else

```r
a <- 330
b <- 200
if(b>a){  
	print("b is greater than a")
}else{  
	print("a is greater than b")
}
```

### else if & else

```r
a<-33
b<-200
if(b>a){
  print("b is greater than a")
}else if(a>b){
  print("a is greater than b")
}else{
  print("a is equal to b")
}
```

### Example: Largest of 3 numbers

```r
#greatest of three numbers with user input
{
a=readline("enter 1st number:")
b=readline("enter 2nd number:")
c=readline("enter 3rd nummber:")
if((a>b)&&(b>c)){
  print("b is greatest number")
}else if((a<b)&&(c<b)){
  print("b is greatest number")
}else{
  print("a is greatest number ")
}}
```

## Switch

Within Switch case
Parameter 1 = condition, 2nd parameter = cases

```r
a= "12"
#Parameter 1 = condition, 2nd parameter = cases
y=switch(a,
         "9" = "hello a",
         "12" = "hello b",
         "18" = "hello c",
         "21" = "hello d"
)
y
```

### Example 3

```r
{
x=readline("1 or 2?:")
y=readline("1 or 2?:")
xy=switch(
  paste(x,y,sep=""),
  "11"="hello xy=11",
  "12"="hello xy=12",
  "21"="hello xy=21",
  "22"="hello xy=22"
)
xy
}
```

# Assignment 2

Design simple calculator using switch case.
Number, operator, operand should be from user
Print full answer

```r
{
a=readline("enter a number:")
b=readline("enter another number:")
d=readline("enter an operation:")
calculation=switch(paste(d),
                   "+"="a+b",
                   "-"="a-b",
                   "*"="a*b",
                   "/"="a/b"
)
calculation
if(a+b){
  d=a+b
  print(d)
}else if(a-b){
  d=a-b
  print(d)
}else if(a*b){
  d=a*b
  print(d)
}else{
  d=a/b
  print(d)
}
}
```

```r
{
A=readline("enter a number:")
a=as.integer(A)
B=readline("enter another number:")
b=as.integer(B)
d=readline("enter an operation:")
calculation=switch(paste(d),
                   "+"="addition of a and b",
                   "-"="subtraction of a and b",
                   "*"="multiplication of a and b",
                   "/"="division of a and b"
)
calculation
if(calculation=+){
  e=a+b
  sprintf("%s=%d",calculation,e)
}else if(calculation=-){
  e=a-b
  sprintf("%s=%d",calculation,e)
}else if(calculation=*){
  e=a*b
  sprintf("%s=%d",calculation,e)
}else if(calcultaion=/){
  e=a/b
  sprintf("%s=%d",calculation,e)
}
}
```

# Day 3

# Data Visualisation

## Pie

ESA Question: Make a pie chart with minimum 6 attributes

```r
a=c(20,35,10,90)

pie(a)
pie(a, labels=a)
pie(a, labels=c("A","B","C","D"))
pie(a, labels=a, col=c("red","blue","green","yellow"))
pie(a, labels=a, col=c("red","blue","green","yellow"), init.angle = 25, density = 29)
pie(a, labels=a, col=c("red","blue","green","yellow"), init.angle = 25, density = 29, angle=c(20,45,12,10))
#init angle is to change the initial angle
#angle is to change the angles of the shading lines(Density)
pie(a, labels=a, col=c("red","blue","green","yellow"), init.angle = 25, density = 29, angle=c(20,45,12,10), border="red")
#changed the border color
pie(a, labels=a, col=c("red","blue","green","yellow"), init.angle = 25, density = 29, angle=c(20,45,12,10), lty=2)

png(filename="hi1.png")#to create a png file in the current working directory to store the pie chart
pie(a, labels=a, col=c("red","blue","green","yellow"), init.angle = 25, density = 29, angle=c(20,45,12,10), main="PIE CHART")
#main gives a title to the plot
#lty changes line type
```

| **Attribute/command** | **Notes** |
| --- | --- |
| pie (a) | Creates pie chart |
| labels = a | Uses values from a as labels |
| col=c("red","blue","green","yellow") | Assigns each colour to a value |
| init.angle = 25 | To change the initial angle |
| density = 29 | The density of the shading lines  |
| angle=c(20,45,12,10) | To change the angles of the shading lines(Density) |
| border="red" | Changes border colour |
| lty=2 | Line type |
| main="PIE CHART” | Title of the plot |
| png(filename="hi1.png") | Creates a png file in the current working directory to store the pie chart.
Needs to be before pie function |
| dev.off() | To let the system know that we are done with the plotting and now we can save it in the png file we created |

![Screenshot 2023-07-27 at 11.57.28 AM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_11.57.28_AM.png)

```r
b=c("s1","s2","s3","s4")
legend("topleft", b, fill=c("red","blue","green","yellow"))#b should always be of character type
legend("topleft", b, fill=c("red","blue","green","yellow"), cex=0.2)#cex is to change the size
```

| legend() | Creates a legend |
| --- | --- |
| legend(”topleft”) | Location of legend |
| fill=c("red","blue","green","yellow") | Colours of the boxes of the legend |
| cex=0.2 | To change the size |

![Screenshot 2023-07-27 at 11.57.55 AM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_11.57.55_AM.png)

### Using plotly

```r
fig <- plot_ly  (mtcars, labels= ~hp, values = ~disp, type = "pie")
fig
```

![Screenshot 2023-07-27 at 11.54.32 AM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_11.54.32_AM.png)

## 3D Pie

- Library to be installed: plotrix

```r
install.packages("plotrix")
library(plotrix)

a=c(20,35,10,90)
pie3D(a, labels=a)
#initial angle for pie3d doesn't work
pie3D(a, labels=a, theta=2)#changes the orientation
pie3D(a, labels=a, radius=1, height=1)
pie3D(a, labels=a, explode=1)#seperates into segments
pie3D(a, labels=a, height=0.5, radius =1, explode=1, theta=0.5)
```

| **Attribute** | **Note** |
| --- | --- |
| pie3D(a) |  |
| labels=a | Uses values from a as labels |
| theta=2 | Changes the orientation. Initial angle for pie3d doesn't work |
| radius=1, height=1 |  |
| explode=1 | Seperates into segments |

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%206.png)

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%207.png)

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%208.png)

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%209.png)

![Untitled](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Untitled%2010.png)

### Plotting a dataset

```r
pie(mtcars$gear)
pie3D(mtcars$gear, labels=mtcars$disp)
```

![Screenshot 2023-07-27 at 12.24.52 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_12.24.52_PM.png)

![Screenshot 2023-07-27 at 12.32.37 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_12.32.37_PM.png)

## Bar Plot

```r
#BARPLOT

x<-c(2,4,6,8)
y<-c("A","B","C","D")

barplot(x)
barplot(x, names.arg=y, main="Barplot", xlab="Names", ylab="No.s", width=c(3,2,1,4))
#names.arg gives the names to the bars
#main gives the title
#xlab displays the name of the x parameter and y lab of y
#width sets the width of the bars
barplot(x, names.arg=y, main="Barplot", xlab="Names", ylab="No.s", horiz=TRUE)
#horiz is to change the bar plot into a horizontal one

```

| **Attributes** |  |
| --- | --- |
| barplot (x) |  |
| names.arg=y | gives the names to the bars |
| main="Barplot" | gives the title |
| col=c("green","pink","yellow") |  |
| xlab="Names", ylab="No.s" | xlab displays the name of the x parameter and y lab of y |
| width=c(3,2,1,4) | sets the width of the bars |
| horiz=TRUE | To change the bar plot into a horizontal one |
| as.matrix(y1) | to plot a stacked bar plot we need to enter the values in matrix format |

![Screenshot 2023-07-27 at 12.40.12 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_12.40.12_PM.png)

![Screenshot 2023-07-27 at 12.40.27 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_12.40.27_PM.png)

```r
#to plot a stacked bar plot we need to enter the values in matrix format
y1=matrix(c(12,23,34,34,54,40,56,78,90,123,124,111), ncol=4,nrow=3)

barplot(as.matrix(y1),col=c("green","pink","yellow"), names.arg=y,main="barplot")
```

![Screenshot 2023-07-27 at 12.41.52 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_12.41.52_PM.png)

## Histogram

```r
#HISTOGRAM

v<-c(19,34,12,56,19,21,32,23,34,56,56,34,58,18,45,45,46)
hist(v,xlab="No. of articles", col="green", border="black")
hist(v,xlab="No. of articles", col="green", border="black", breaks=2)
#breaks the number of times you've given
```

| **Attributes** | **Notes** |
| --- | --- |
| xlab="No. of articles"
ylab=”” | x and y axis labels |
| col="green" |  |
| border="black" |  |
| breaks=2 | Breaks the number of times you've given |

![Screenshot 2023-07-27 at 12.57.02 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_12.57.02_PM.png)

![Screenshot 2023-07-27 at 12.57.46 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_12.57.46_PM.png)

## Line Graph

```r
#LINE GRAPH

v<-c(13,22,28,7,31)
w<-c(11,13,32,6,35)
x<-c(12,22,15,34,35)

plot(v)#gives a scatter plot
plot(v, type="l")#gives the line graph
plot(v,type="o")#combination of scatter and line plots
plot(v,type="b",lty=2)#run to see how it looks
plot(v,type="o", lwd=2)#lwd sets the width of the line
plot(v,type="p")#same as default plot v
plot(v,type="s")#stair steps like (vertical lines are the ranges. eg, 13-22)
plot(v,type="S")#stair steps like (horizontal lines are the ranges. eg, 13-22)
plot(v,type="h")#histogram type
plot(v,type="n")#blank
plot(v,type="s",lty=2,lwd=2)

plot(c(v,w,x),type="l")#it will plot all three in the same line
{
plot(v,type="l")
lines(w,type="s",lty=2)
lines(x,type="p")
}#to plot the three values in three diff lines of diff types in the same graph

plot(v,type="l",xlab="a",ylab="b",ylim=c(1,30),xlim=c(1,30))
#ylim and xlim sets the limit range of y and x axis in the graph
```

| **Attribute** | **Note** |
| --- | --- |
| plot(v) | Scatter plot |
| type="l" | line plot |
| type="o" | Combination of line & scatter |
| type="b" | Combination of line & scatter with breaks |
| type="p" | scatter plot, same as plot v |
| type="s" | stairs type, with ranges as vertical lines |
| type="S" | stairs type, with ranges as horizontal lines |
| type="h" | histogram |
| type="n" | blank |
| lty=2 | line type |
| lwd=2 | line width |
| xlab & ylab | x and y axis labels |
| xlim=c(1,30), ylim=c(1,30) | limit range for x and y axis in the graph |

# Loops

## for loop

```r
week<-c('Mon','Tue','Wed','Thurs','Fri','Sat','Sun')
for(val in week)
{
  print(val)
}
```

### For lists

- keyword: seq_along
- for accessing the list, double box brackets [[i]]

```r
# Create a list of numbers
my_list <- list(1, 2, 3, 4, 5)
 
# Loop through the list and print each element
for (i in seq_along(my_list)) {
  current_element <- my_list[[i]]
  print(paste("The current element is:", current_element))
}
```

### For matrix

- Keyword: seq_len

```r
# Create a 3x3 matrix of integers
my_matrix <- matrix(1:9, nrow = 3)
 
# Loop through the matrix and print each element
for (i in seq_len(nrow(my_matrix))) {
  for (j in seq_len(ncol(my_matrix))) {
    current_element <- my_matrix[i, j]
    print(paste("The current element is:", current_element))
  }
}
```

## while loop

```r
i <- 1while (i < 6) {  
	print(i)  
	i <- i + 1
}
```

# Functions

```r
fname<-function(){
  print("hello")
}
fname()
```

```r
myfunc<-function(f){
  paste(f,"college")
}
myfunc("PES")
```

# Day 4

## Scatter Plots

```r
#Scatter Plots
x <- c(141, 134, 200, 156, 108, 116, 55, 143, 16)
y <- c(62,85,56, 21, 47, 17,76, 92, 58)

plot(x = x, xlab="weight", ylab = "Milage", main = "weight v/s milage")
```

![Screenshot 2023-07-27 at 9.35.10 AM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_9.35.10_AM.png)

### Scatterplot Matrix

```r
#Scatter Plots
x <- c(141, 134, 200, 156, 108, 116, 55, 143, 16)
y <- c(62, 85, 56, 21, 47, 17, 76, 92, 58)

plot(x = x, xlab="weight", ylab = "Milage", main = "weight v/s milage")
pairs(~x+y)
#No of values (length) of x and y datasets should be equal
```

![Screenshot 2023-07-27 at 9.32.12 AM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_9.32.12_AM.png)

Each column gives x-axis and every row gives y-axis 

```r
#Scatter plots with pairs
pairs(~x+y)
pairs(~wt +mpg +disp +cyl, data=mtcars, main = "Scatterplot matrix")
```

![Screenshot 2023-07-27 at 9.39.47 AM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_9.39.47_AM.png)

## Graphical Plot

## ggplot

- Library to be installed: ggplot2

```r
install.packages("ggplot2")
library(ggplot2)
ggplot()
ggplot(data = mtcars, aes(x = hp, y=mpg, col= hp))+geom_point() #color based on column hp
labs(title = "Miles per Gallon vs Horsepower", x= "Horsepower", y="Gallon")

ggplot(data = mtcars, aes(x = hp, y=mpg))+geom_area() 
#aes = aesthetic
```

| **Attributes** |  |
| --- | --- |
| (data = mtcars) |  |
| (aes(x = hp, y=mpg, col= hp)) | aes= aesthetic |
| (+geom_point()) |  |
| labs() |  |

**Note: For ggplot, for colour its col (within aes)**
in plotly, its color

![Screenshot 2023-07-27 at 2.16.41 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_2.16.41_PM.png)

![Screenshot 2023-07-27 at 2.17.10 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_2.17.10_PM.png)

## plotly

- Library to be installed: plotly

```r
install.packages("plotly")
library(plotly)
fig <- plot_ly (data = mtcars, x = ~disp, y = ~hp) 
#For column name always give ~ before
fig
```

```r
data("iris")
fig <- plot_ly(data = iris, x= ~Sepal.Length, y = ~Petal.Length, symbol= ~Species, symbols= c('circle','x','o') )
fig
#symbol selects the column for which we're working on
#symbols is used for assigning symbols (circle, cross, hollow circle)
```

![Screenshot 2023-07-27 at 10.43.24 AM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_10.43.24_AM.png)

| **Attribute** |  |
| --- | --- |
| data = mtcars |  |
| x=~hp, y=~disp |  |
| symbol = ~ |  |
- Trace - Helps us in plotting properly

```r
add_trace(fig, type="scatter", mode="markers+lines")
```

| **Attributes** | **Notes** |
| --- | --- |
| add_trace(x) |  |
| type= ”scatter” |  |
| mode = “markers+lines” |  |

![Screenshot 2023-07-27 at 10.42.19 AM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_10.42.19_AM.png)

## 3D Scatter Plot

```r
attach(mtcars)
fig <- plot_ly (data = mtcars, x = ~mpg, y = ~hp, z=~cyl, color=~hp,                
								colors = c("red","orange","blue")) 
#For column name always give ~ before
#If you dont give hp, it wont give multiple colours. hp gives shade bar
fig
```

![Screenshot 2023-07-27 at 2.33.45 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_2.33.45_PM.png)

### Plotly for pie chart

```r
fig <- plot_ly  (mtcars, labels= ~hp, values = ~disp, type = "pie")
fig
```

![Screenshot 2023-07-27 at 2.34.59 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_2.34.59_PM.png)

### Plotly for barplot

```r
max.temp = c(22,27,33,26,24,18,20)
barplot(max.temp, main = "Max temps in a week", )
```

## Dataset

```r
?mtcars #Shows all deatils, for detailed study of the dataset
summary(mtcars)
```

```r
names(mtcars)[1:10]
names(mtcars[1:10])

rownames(mtcars)
rownames(mtcars)[which.max(mtcars$hp)]
rownames(mtcars)[which.min(mtcars$hp)]
```

```r
Data_Cars <- mtcars

dim(Data_Cars) #Dimension of dataset

mean(Data_Cars$wt)
median(Data_Cars$wt)

sort(table(mtcars$wt))
#with minus the order is reversed
sort(-table(mtcars$wt)) #Sorts according to frequency 
names(sort(-table(mtcars$wt))) #Makes it into names (strings)
```

# Day 5

## Box Plot

```r
boxplot(mpg ~ carb, data = mtcars, xlab = "carbs", ylab = "mpg", 
				main = "R Boxplot Example")
```

```r
boxplot(mpg ~ carb, data = mtcars, xlab = "carbs", ylab = "mpg", 
				notch = TRUE, #Narrowing of box at median        
				main = "R Boxplot Example")
```

![Screenshot 2023-07-27 at 9.51.13 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_9.51.13_PM.png)

![Screenshot 2023-07-27 at 9.51.25 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_9.51.25_PM.png)

| **Attribute** | Notes |
| --- | --- |
| boxplot(mpg ~ carb) | The 2 variables at x and y axis that are used for plotting |
| data = mtcars |  |
| xlab, ylab | labels at x and y axis |
| notch = TRUE | Narrowing of box at median  |
| main | title of boxplot |

## Violin Plot

```r
install.packages("vioplot")
library(vioplot)

x1 = mtcars$mpg[mtcars$cyl==4]
x2 = mtcars$mpg[mtcars$cyl==6]
x3 = mtcars$mpg[mtcars$cyl==8]
vioplot(x1,x2,x3, names = c("4 Cyl","6 Cyl","8 Cyl"))
title("Violin plot example")
```

![Screenshot 2023-07-27 at 9.57.12 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_9.57.12_PM.png)

## Bag plot

```r
install.packages("aplpack")
library(aplpack)

attach(mtcars)
bagplot(disp,hp, xlab = "Car Weight", ylab = "Miles per gallon", 
				main = "2D box plot extention")
```

![Screenshot 2023-07-27 at 10.07.26 PM.png](R%20Programming%20cb9e6798767f4beaa20fb425b009a881/Screenshot_2023-07-27_at_10.07.26_PM.png)