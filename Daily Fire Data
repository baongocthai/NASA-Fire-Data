library(readr)
library(stringr)

#set working directory
setwd("D:/Backtrajectory/Backtrajectory")

#import data: change the file name below
fire_nov <- read_csv("Fire data/DL_FIRE_M-C61_241306/fire_nrt_M-C61_241306.csv")
fire = data.frame(matrix(ncol = 3,nrow = nrow(fire_nov)))
colnames(fire) = c("longitude","latitude","satellite")

#create date sequence: change the date as the fire duration data downloaded
Date = as.data.frame(seq(as.Date("2021-12-01", tz="UTC"), 
                             as.Date("2021-12-31",tz="UTC")
                         , by="day"))

#only take longitude, lattitude, satellite & acquired date
fire$longitude = fire_nov$longitude
fire$latitude = fire_nov$latitude
fire$satellite = fire_nov$satellite
fire$Date = fire_nov$acq_date
fire$longitude = round(fire$longitude,digits = 3)
fire$latitude = round(fire$latitude,digits = 3)

#separate and write into different csv files
for (i in 1:nrow(Date)) {
  requiredDate = Date[i,1]
  subSet = subset(fire,Date == requiredDate)
  name = str_remove_all(requiredDate,"-")
  write.table(subSet[,1:2], file = paste("fire","_",name,".txt",sep=""),
            row.names = FALSE,sep = " ")
  print(i)
}
