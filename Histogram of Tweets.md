SELECT 
  tweet_num AS tweet_bucket,
  COUNT(user_id) AS user_num
FROM
  (SELECT 
    user_id,
    COUNT(tweet_id) AS tweet_num
  FROM tweets
  WHERE tweet_date BETWEEN '01/01/2022' AND '12/31/2022'
  GROUP BY user_id) AS total_tweet
GROUP BY tweet_num;
