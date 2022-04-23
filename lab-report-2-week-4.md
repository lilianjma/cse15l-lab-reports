Lab 2 Report
1. Show ss of code change
2. Link to file that causes error
3. Show symptom of file
4. 2-3 sentences describing relationship between bug, symptom, and failure inducing file  


## Change 1
**Screenshot of code change:**

<img width="1217" alt="Screen Shot 2022-04-23 at 4 12 30 PM" src="https://user-images.githubusercontent.com/31358827/164949035-8fbc956b-0064-4102-9134-8660cb00f613.png">

*Note: I didn't commit after each change so change 1 and 2 are in the same commit are both in the same commit. The second change was that I added the second if statement and put the toReturn.add line in it.*


**Link to file that causes error:**  

[test-file2-mine.md](https://github.com/lilianjma/markdown-parser/blob/main/test-file2-mine.md)

**Symptom of that file:**  

<img width="1207" alt="Screen Shot 2022-04-23 at 3 57 41 PM" src="https://user-images.githubusercontent.com/31358827/164948731-21cc3089-39b7-4cd5-9bee-c43a124d24e8.png">

**2-3 sentences:** 

The bug was that the code did not check if there was a case that there wasn't any brackets or parenthesis which occurs in the error inducing file, causing the .indexOf call to return -1. This caused an index out of bounds symptom.



## Change 2
**Screenshot of code change:**  

<img width="1217" alt="Screen Shot 2022-04-23 at 4 12 30 PM" src="https://user-images.githubusercontent.com/31358827/164949035-8fbc956b-0064-4102-9134-8660cb00f613.png">

*Note: I didn't commit after each change so change 1 and 2 are in the same commit are both in the same commit. The second change was that I added the second if statement and put the toReturn.add line in it.*  


**Link to file that causes error:**

[test-file3-mine.md](https://github.com/lilianjma/markdown-parser/blob/main/test-file3-mine.md)

**Symptom of that file:**

<img width="1207" alt="Screen Shot 2022-04-23 at 3 52 25 PM" src="https://user-images.githubusercontent.com/31358827/164948618-411b8f37-1490-437b-a98e-93845d297d09.png">


**2-3 sentences:**

The bug was that the file would not check if the parenthesis had nothing in them. The symptom that the failure inducing file caused was that the false "links" would be empty strings.


## Change 3 

**Screenshot of code change:**

<img width="1072" alt="Screen Shot 2022-04-23 at 12 48 45 PM" src="https://user-images.githubusercontent.com/31358827/164943970-9c679ad6-5be9-484a-aaa4-2fe641191a74.png">


**Link to file that causes error:**

My code was failing [test-file7](test-file7.md) and [test-file8](test-file8.md). To fix this I added 


**Symptom of that file:**

<img width="1207" alt="Screen Shot 2022-04-23 at 4 02 46 PM" src="https://user-images.githubusercontent.com/31358827/164948840-8d0031d5-cd9b-4d60-a430-e63d81059ef1.png">


**2-3 sentences:**

The bug was that the code did not check if the opening brackets were after the closing brackets or if the opening parenthesis were after the closing parenthesis which occured in the error inducing file. This symptom this caused using the error inducing file as the input was that there would be an infinite loop. 

