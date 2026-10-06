facebook_data <- read.csv("pseudo_facebook.csv")
dim(facebook_data)
names(facebook_data)
str(facebook_data)
colSums(is.na(facebook_data))
sum(duplicated(facebook_data))

# Handle missing values

facebook_data$gender[is.na(facebook_data$gender)] <- "Unknown"

facebook_data$tenure[is.na(facebook_data$tenure)] <- median(
  facebook_data$tenure,
  na.rm = TRUE
)

# Check missing values again
colSums(is.na(facebook_data))
dim(facebook_data)
summary(facebook_data)
table(facebook_data$gender)
# Gender Distribution

gender_count <- table(facebook_data$gender)

barplot(
  gender_count,
  main = "Gender Distribution of Facebook Users",
  xlab = "Gender",
  ylab = "Number of Users"
  
)
hist(
  facebook_data$age,
  main = "Age Distribution of Facebook Users",
  xlab = "Age",
  ylab = "Number of Users"
)

hist(
  facebook_data$friend_count,
  main = "Friend Count Distribution",
  xlab = "Number of Friends",
  ylab = "Number of Users"
)

hist(
  facebook_data$likes_received,
  main = "Distribution of Likes Received",
  xlab = "Likes Received",
  ylab = "Number of Users"
)

boxplot(
  likes_received ~ gender,
  data = facebook_data,
  main = "Likes Received by Gender",
  xlab = "Gender",
  ylab = "Likes Received"
)
plot(
  facebook_data$friend_count,
  facebook_data$likes_received,
  main = "Friend Count vs Likes Received",
  xlab = "Friend Count",
  ylab = "Likes Received"
)

cor(
  facebook_data$friend_count,
  facebook_data$likes_received
)

cor(
  facebook_data$friendships_initiated,
  facebook_data$friend_count
)

id <- facebook_data$mobile_likes
web <- facebook_data$www_likes

sum_mobile_likes <- sum(id)
sum_web_likes <- sum(web)

c(
  Mobile_Likes = sum_mobile_likes,
  Web_Likes = sum_web_likes
)
mobile_web_ratio <- sum_mobile_likes / sum_web_likes

mobile_web_ratio



mobile_received <- sum(facebook_data$mobile_likes_received)
web_received <- sum(facebook_data$www_likes_received)

c(
  Mobile_Likes_Received = mobile_received,
  Web_Likes_Received = web_received
)

received_ratio <- mobile_received / web_received

received_ratio

top_users <- facebook_data[
  order(facebook_data$likes_received, decreasing = TRUE),
  c("userid", "age", "gender", "friend_count", "likes_received")
]

head(top_users, 10)

top10 <- head(top_users, 10)

barplot(
  top10$likes_received,
  names.arg = top10$userid,
  main = "Top 10 Users by Likes Received",
  xlab = "User ID",
  ylab = "Likes Received",
  las = 2
)


facebook_data$age_group <- cut(
  facebook_data$age,
  breaks = c(0, 17, 25, 35, 50, 100, Inf),
  labels = c(
    "Under 18",
    "18-25",
    "26-35",
    "36-50",
    "51-100",
    "100+"
  ),
  right = TRUE
)

table(facebook_data$age_group)

id="2lq7xv"
sum(facebook_data$age > 100)

unique(facebook_data$age[facebook_data$age > 100])

sum(facebook_data$age > 100)

age_group_count <- table(facebook_data$age_group)

barplot(
  age_group_count,
  main = "Facebook Users by Age Group",
  xlab = "Age Group",
  ylab = "Number of Users"
)


aggregate(
  friend_count ~ gender,
  data = facebook_data,
  FUN = mean
)



id="f9k2qa"
avg_friends_gender <- aggregate(
  friend_count ~ gender,
  data = facebook_data,
  FUN = mean
)

barplot(
  avg_friends_gender$friend_count,
  names.arg = avg_friends_gender$gender,
  main = "Average Friend Count by Gender",
  xlab = "Gender",
  ylab = "Average Number of Friends"
)


avg_likes_gender <- aggregate(
  likes_received ~ gender,
  data = facebook_data,
  FUN = mean
)

avg_likes_gender


barplot(
  avg_likes_gender$likes_received,
  names.arg = avg_likes_gender$gender,
  main = "Average Likes Received by Gender",
  xlab = "Gender",
  ylab = "Average Likes Received"
)

plot(
  facebook_data$friend_count,
  facebook_data$likes_received,
  main = "Friend Count vs Likes Received",
  xlab = "Number of Friends",
  ylab = "Likes Received",
  pch = 19
)

avg_likes_age <- aggregate(
  likes_received ~ age_group,
  data = facebook_data,
  FUN = mean
)

avg_likes_age


barplot(
  avg_likes_age$likes_received,
  names.arg = avg_likes_age$age_group,
  main = "Average Likes Received by Age Group",
  xlab = "Age Group",
  ylab = "Average Likes Received"
)



mobile_total <- sum(facebook_data$mobile_likes)
web_total <- sum(facebook_data$www_likes)

total_likes <- mobile_total + web_total

mobile_percentage <- (mobile_total / total_likes) * 100
web_percentage <- (web_total / total_likes) * 100

mobile_percentage
web_percentage

likes_source <- c(
  Mobile = mobile_total,
  Web = web_total
)

pie(
  likes_source,
  main = "Distribution of Likes by Platform"
)

correlation_friendships <- cor(
  facebook_data$friendships_initiated,
  facebook_data$friend_count
)

correlation_friendships


plot(
  facebook_data$friendships_initiated,
  facebook_data$friend_count,
  main = "Friendships Initiated vs Friend Count",
  xlab = "Friendships Initiated",
  ylab = "Friend Count",
  pch = 19
)



avg_friends_age <- aggregate(
  friend_count ~ age_group,
  data = facebook_data,
  FUN = mean
)

avg_friends_age


par(mfrow = c(2, 2))

# Plot 1: Age distribution
hist(
  facebook_data$age,
  main = "Age Distribution",
  xlab = "Age",
  ylab = "Number of Users"
)

# Plot 2: Friend count distribution
hist(
  facebook_data$friend_count,
  main = "Friend Count Distribution",
  xlab = "Number of Friends",
  ylab = "Number of Users"
)

# Plot 3: Average likes by gender
barplot(
  avg_likes_gender$likes_received,
  names.arg = avg_likes_gender$gender,
  main = "Average Likes by Gender",
  xlab = "Gender",
  ylab = "Average Likes"
)

# Plot 4: Average likes by age group
barplot(
  avg_likes_age$likes_received,
  names.arg = avg_likes_age$age_group,
  main = "Average Likes by Age Group",
  xlab = "Age Group",
  ylab = "Average Likes"
)

par(mfrow = c(1, 1))

barplot(
  avg_friends_gender$friend_count,
  names.arg = avg_friends_gender$gender,
  main = "Average Friend Count by Gender",
  xlab = "Gender",
  ylab = "Average Number of Friends"
)


gender_counts <- table(facebook_data$gender)

gender_counts



colSums(is.na(facebook_data))


write.csv(
  facebook_data,
  "facebook_data_cleaned.csv",
  row.names = FALSE
)



id="n7w4kp"
summary(facebook_data)

overall_means <- c(
  Average_Age = mean(facebook_data$age),
  Average_Friends = mean(facebook_data$friend_count),
  Average_Friendships_Initiated = mean(facebook_data$friendships_initiated),
  Average_Likes = mean(facebook_data$likes),
  Average_Likes_Received = mean(facebook_data$likes_received)
)

overall_means




final_results <- data.frame(
  Metric = c(
    "Total Users",
    "Average Age",
    "Average Friends",
    "Average Friendships Initiated",
    "Average Likes Given",
    "Average Likes Received",
    "Mobile Likes Percentage",
    "Web Likes Percentage",
    "Friend Count vs Likes Received Correlation",
    "Friendships Initiated vs Friend Count Correlation"
  ),
  Value = c(
    nrow(facebook_data),
    mean(facebook_data$age),
    mean(facebook_data$friend_count),
    mean(facebook_data$friendships_initiated),
    mean(facebook_data$likes),
    mean(facebook_data$likes_received),
    mobile_percentage,
    web_percentage,
    cor(facebook_data$friend_count, facebook_data$likes_received),
    correlation_friendships
  )
)

write.csv(final_results, "facebook_final_results.csv", row.names = FALSE)

final_results


file.exists("facebook_final_results.csv")