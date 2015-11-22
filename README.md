# Read Me 


## Raw data

- 'train/X_train.txt': Training set.

- 'train/y_train.txt': Training labels.

- 'test/X_test.txt': Test set.

- 'test/y_test.txt': Test labels.


## Code Description

#### Loading dplyr Package
library(dplyr)

#### Reading Test data Set

test_main<-read.table("./test/X_test.txt",header = F,sep = "")
test_labels<-read.table("./test/y_test.txt",header = F,sep = "")
test_subjects<-read.table("./test/subject_test.txt",header = F,sep = "")
test_main$label<- test_labels$V1
test_main$subject<- test_subjects$V1

#### Reading Training data Set

train_main<-read.table("./train/X_train.txt",header = F,sep = "")
train_labels<-read.table("./train/y_train.txt",header = F,sep = "")
train_subjects<-read.table("./train/subject_train.txt",header = F,sep = "")
train_main$label<- train_labels$V1
train_main$subject<- train_subjects$V1

#### Merging Test and Training Data Set

FinalMerge<-merge(test_main,train_main,all=T)

#### Keeping only variables need for data Analysis

Part2_data<-select(FinalMerge,V1:V6)
Part2_data$label<-FinalMerge$label
Part2_data$subject<-FinalMerge$subject

#### Descriptive Label added to Label Variable

Part3_data<-Part2_data
Part3_data$label<-factor(Part3_data$label,levels = c(1,2,3,4,5,6) ,
                       labels = c("WALKING","WALKING_UPSTAIRS",
                                  "WALKING_DOWNSTAIRS"
                                  ,"SITTING","STANDING","LAYING"))

#### Renaming Variable vs Default

Part4_data<-Part3_data
Part4_data<-rename(Part4_data,tBodyAcc_mean_X = V1,tBodyAcc_mean_Y = V2,
                   tBodyAcc_mean_Z = V3, tBodyAcc_std_X = V4, 
                   tBodyAcc_std_Y = V5,tBodyAcc_std_Z = V6)


#### Summarizing Data for each activity and subject

Part5_data<-Part4_data

activity<-group_by(Part5_data,label)
summarydata1<-summarise(activity,tBodyAcc_mean_X = mean(tBodyAcc_mean_X),
          tBodyAcc_mean_Y = mean(tBodyAcc_mean_Y),
          tBodyAcc_mean_Z = mean(tBodyAcc_mean_Z),
          tBodyAcc_std_X  = mean(tBodyAcc_std_X),
          tBodyAcc_std_Y = mean(tBodyAcc_std_Y),
          tBodyAcc_std_Z = mean(tBodyAcc_std_Z))

Subject_Type<-group_by(Part5_data,subject)
summarydata2<-summarise(Subject_Type,tBodyAcc_mean_X = mean(tBodyAcc_mean_X),
                        tBodyAcc_mean_Y = mean(tBodyAcc_mean_Y),
                        tBodyAcc_mean_Z = mean(tBodyAcc_mean_Z),
                        tBodyAcc_std_X  = mean(tBodyAcc_std_X),
                        tBodyAcc_std_Y = mean(tBodyAcc_std_Y),
                        tBodyAcc_std_Z = mean(tBodyAcc_std_Z))

#### Final Merging of Summary Reports

FinalMergeSumm<-merge(summarydata1,summarydata2,all=T)
head(FinalMergeSumm)

#### Write Text data report

write.table(FinalMergeSumm,file = "Final_Summary_Report.txt",sep="  ",row.names = F)
