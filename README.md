# Hello_World-README.md
df<-read.csv("office_employees.csv",
             stringsAsFactors=FALSE) # Do not read strings as factors - factor store the categorical data


## Duplicate Records ##
#                         Redundant data can be caused by human error or poor IS design
# Takes up unnecessary memory and may introduce bias to analyses
?duplicated # Returns logical vector with TRUE for elements/rows that are
# an exact duplicate of a previous element
duplicated(df)
sum(duplicated(df)) # 2 duplicate records           sum the number of true ( 1=t, 0=f)

# 2 approaches to remove duplicates
# Use logical vector and ! to negate
df<-df[!duplicated(df), ]         #return without the dulicated

# Or use unique() function:
?unique # Extract unique elements/rows
df<-unique(df)                # the unique values   its the same thing as remove the duplicate




# What about near-duplicates? 
# Check for multiple rows with same employee name:
?table # Calculate frequency counts
table(df$Employee)                       # table of counts 

# Sort frequency table for easier reading:
sort(table(df$Employee), decreasing=TRUE)          # put the repeating the name at the bneginning 

# There are two employee records for Meredith Palmer
# Check records under name Meredith Palmer:
df[which(df$Employee=="Meredith Palmer"),]           # check the records of Meredith

# Records are exactly the same except for age

# Can also use duplicated() to find repeating values in a
# specific column
duplicated(df$Employee)       # assume age 47 is correct
## Exercise ##
# Use the results of duplicated() to remove duplicate records
# for employees with the same name
df = df[!duplicated(df$Employee),]  
