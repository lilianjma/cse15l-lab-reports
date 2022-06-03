### How you found the tests with different results?  
I searched through using vim diff.  

# TEST FILE 495
[link to file](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/495.md)  

### My MarkdownParser results:  
<img width="128" alt="Screen Shot 2022-06-02 at 3 47 42 PM" src="https://user-images.githubusercontent.com/31358827/171750608-e4afbacb-f7b1-457e-85f6-bcb4474de98e.png">

### Their MarkdownParser results:  
<img width="119" alt="Screen Shot 2022-06-02 at 3 49 23 PM" src="https://user-images.githubusercontent.com/31358827/171750793-75fe7a46-0882-43a3-8a37-537602aa62ff.png">    

***Describe which implementation is correct***  
Their implementation is correct.  

***Corect output:***  
`[foo(and(bar))]`

***For the implementation that’s not correct (or choose one if both are incorrect), describe the bug (the problem in the code) in about 2-3 sentences. You don’t have to provide a fix, but you should be specific about what is wrong with the program, and show the code that should be fixed (Provide a screenshot of code and highlight where the change needs to be made).***  

The bug is that it finds the first instance of the closed bracket. Something that could fix it for this test file is a while loop after the highlighted line that finds the last instance of a closing bracket as long as the closing brackets are next to each other.  

Screenshot:  
<img width="679" alt="Screen Shot 2022-06-02 at 5 34 22 PM" src="https://user-images.githubusercontent.com/31358827/171762217-47a34c18-2f41-4c02-b767-b662ff825139.png">

 
# TEST FILE 494  
[link to file](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/494.md)  
### My MarkdownParser results:   
<img width="124" alt="Screen Shot 2022-06-02 at 3 48 05 PM" src="https://user-images.githubusercontent.com/31358827/171750640-afe3af15-ad8e-4858-a214-af53edf91afa.png">  

### Their MarkdownParser results:  
<img width="74" alt="Screen Shot 2022-06-02 at 5 05 39 PM" src="https://user-images.githubusercontent.com/31358827/171759855-964ae88d-aa81-4304-9211-2268f8fda230.png">

### Questions
***Describe which implementation is correct***  
Their implementation is correct.

***Coreect output:***  
`[(foo)]`  

***For the implementation that’s not correct (or choose one if both are incorrect), describe the bug (the problem in the code) in about 2-3 sentences. You don’t have to provide a fix, but you should be specific about what is wrong with the program, and show the code that should be fixed (Provide a screenshot of code and highlight where the change needs to be made).***

For their MarkdownParser, they do not check for back slashes before certain characters like (). This could be fixed by adding a helper method that modifies the link if neccissary and returns it. This helper method would be called at the highlighted area with the input as the highlighted variable.  

Screenshot:  
<img width="724" alt="Screen Shot 2022-06-02 at 5 40 17 PM" src="https://user-images.githubusercontent.com/31358827/171762710-7f6c7455-c8ec-4a4a-ab5e-4102fa382013.png">

