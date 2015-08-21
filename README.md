# G-PUserDataFromTwitter


Hello, whoever saw this:


There are three problems I fixed:

1. problem: Extra data: line 2 column 1 - line 12 column 1 (char 1282269 - 8011689) in twitter.json
    Working on <open file '/Users/HanyeWei/Documents/RA/user-timeline-tools/config/folder//twitterapi.json', mode 'r' at 0x107fb0660> 

method: use for loop to readline instead of just read whole file into one paragraph to process.
code:   line 375   for line in f:


2. >>>> Warning: Could not add User: 1366 (HY000): Incorrect integer value: '' for column 'followers' at row 1
    Query: INSERT INTO users_user (twitter_id, twitter_name, fullname, followers, following, favorites, tweets, timezone) VALUES('357750891', '', '', '', '', '', '', '' )

method: the system should not exit if one column is empty, just skip.
code:   line 123  #sys.exit()

3. Traceback (most recent call last):
    File "parseUserTimeline.py", line 390, in <module>
    addUserMentions(conn, tweet)
    File "parseUserTimeline.py", line 265, in addUserMentions
    mention_id,
    UnboundLocalError: local variable 'mention_id' referenced before assignment

method: the system should not exit when the mention_id is empty.
code: 

265         try :
266             user_mention_values = [
267                 mention_id,
268                 user_id
269             ]
270         except :
271             print "error in mention_id"
272             continue




One problem remains to be fixed:

1. >>>> Warning: Could not add Tweet: 1366 (HY000): Incorrect string value: '\xE6\x9D\xA5\xE8\x87\xAA...' for column 'text' at row 1
    Query: INSERT INTO tweets_tweet (tweet_id, created_at, text, source, iso_language) VALUES ('448751230525775872', '2014-03-26 09:20:05', 'I scored 54396 points at 2048, a game where you join numbers to score high! #2048game http://t.co/qzL3YTbDgU 来自 @gabrielecirulli', '<a href=\"https://dev.twitter.com/docs/tfw\" rel=\"nofollow\">Twitter for Websites</a>', 'ja')
    Failed to insert tweets from HanyeWei.json.

cause: foreign language






Fun things I found just in use in one twitter account:


With account twitterapi, it has 2993 tweets. And the average of the tweeting time is 15.7685. The fun thing is after I process the frequency of the twitter time, it shows it has high actively in the afternoon than morning.

The result show below:
+------------------+----------+
| Hour(created_at) | hourFreq |
+------------------+----------+
|               15 |      329 |
|               17 |      323 |
|               16 |      283 |
|               21 |      262 |
|               20 |      246 |
|               19 |      234 |
|               22 |      220 |
|               18 |      203 |
|               14 |      199 |
|               23 |      159 |
|                0 |      113 |
|                1 |       92 |
|               13 |       83 |
|                5 |       49 |
|                2 |       45 |
|                4 |       35 |
|                3 |       33 |
|                7 |       25 |
|                6 |       23 |
|               12 |       12 |
|                8 |        9 |
|               11 |        8 |
|                9 |        6 |
|               10 |        2 |
+------------------+----------+

Based on this timeline, I thought it should be a group of people has very high effiency in the afternoon. 


Futher things like to highlight the keywords in the tweets or find out the relationship between friends or favorites can also be extracted but with more effort.


Thanks


Hanye Wei


