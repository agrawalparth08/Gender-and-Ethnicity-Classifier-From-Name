# Gender-and-Ethnicity-Detection-From-Name
Different approaches combined and amalgamated into code which works on Names dataset from https://mbejda.github.io/

1) Gender Classification <br> <br>
  Mostly Gender relies on the first name and it doesn't matter much on the last name. Also, the dataset which on the site had only some sort of uncleaned Indian names and also differences in naming conventions for a different race. (some had initials, etc)
I removed and tried to bring it to a single word which made it easier to run my hypothesis on. <br> <br>
  A few of the articles helped me understand and validate the logic as well like <br>
  https://sheroes.tech/identifying-user-gender-at-sheroes-women-only-social-platform-a522e2d0f445 <br>
  https://medium.com/simpl-under-the-hood/classifying-gender-based-on-indian-names-in-82f34ce47f6d <br> <br>
  and finally, for features, I decided to input up to first 3 and last 3 letters of a name which tells you how they sound in general (most female names end in vowels like a, i,e) and then ran simple decision tree classifier and SVM to test this which gave me quite a decent accuracy (>95%).

2) Ethnicity classification <br> <br>
I read some literature where people have worked on Florida census data, Wikipedia data and Olympic names data. There are two prominent APIs/SDK in the market namely NamSor and ethnicolr. Ethnicolr is still opensource so before jumping onto the research paper and their implementation, I tried to run a simple word2vec embeddings with lstm on full names (combining first and last names) and tried to see the results. It gave me 75-80% training and test accuracy (avoided overfitting on training by not letting it run for more epochs). But the results were not that satisfactory.<br> <br>
I then tried to fit this data in the ethnicolr code framework where they use 2-gram word vocabs. As they are very hyperparameter centric, the results varied a lot and on trying with 3-gram the accuracy dropped to 45%. 2-gram model worked good but somehow is overfit on black/white people data because it is an unbalanced dataset. I did try to use imblearn but it wasn't much of a help. <br> <br>
I guess with more data and fundamental questions like actually identifying the source language of the name which can only tell us about the origin, it may or may not give us a big-picture view as immigrants and only name data doesn't give us that many features to play around with.
