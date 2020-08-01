# Constructing_Rules_From_Census_Dataset
An approximate solution to this problem
## **Introduction**

The adult.data contain over 30000 rows of demographic information and some of then can combined into groups. For example one person have 'native-country' = 'United-States' and 'capital-gain' = '0'. These attributes can lead to strategic data-driven decisions. Take first 10 line of data as input, we can find the following patterns that identify the groups with no capital gain or loss:

- There are 7 people with {capital-gain=None, capital-loss=None}	
- There are 5 people with {native-country=United-States, capital-gainn=None, capital-loss=None}
- There are 5 people with {native-country=United-States, capital-gain=None}
- There are 8 people with {native-country=United-States, capital-loss=None}

The *support* of the set of attributes in definded as the ratio of "total number of records with the given attributes" to " total number of records in the dataset". For example.

- The support of {capital-gain=None, capital-loss=None}	is 7/10 = 0.7

We can now derive some rules **X=>Y**, where X and Y describe the attributes set. The confidence of the rule is defined as the ratio of "total number of records with the given unique attributes in X and Y" to "total number of records with the given attributes in X", i.e., the ratio of "support of X U Y" to "support of X". For example:

- The confidence of the rule {native-country=United-States, capital-gain=None} =>{capital-loss=None} is 0.5/0/5=1.0
- The confidence of the rule {capital-gain=None, capital-loss=None} =>{native-country=United-States} is 0.5/0/7=0.71



### **Task**
Rearrange the given set of rules X=>Y in descending order of confidence. It is guaranteed that no two rules have the same confidence. Also, the support of the attributes sets X and Y in each of the rules is greater thant or equal to 0.3

### **Function Description**
Complete the *arrangeingRules* function. The function must return a string of the rules in descending order of confidence.

*arrangingRules* has the following parameter:
rules: an array of rules strings

###  **Sample Input**
3\
{native-country=United-States,capital-gain=None}=>{capital-loss=None} \
{capital-gain=None,capital-loss=None}=>{native-country=United-States} \
{native-country=United-States,capital-loss=None}=>{capital-gain=None}

### **Sample Output**
{native-country=United-States,capital-gain=None}=>{capital-loss=None}\
{native-country=United-States,capital-loss=None}=>{capital-gain=None}\
{capital-gain=None,capital-loss=None}=>{native-country=United-States} \

### **Explanation**
- The confidence of {native-country=United-States,capital-gain=None}=>{capital-loss=None} is 0.94
- The confidence of {native-country=United-States,capital-loss=None}=>{capital-gain=None} is 0.9098
- The confidence of {capital-gain=None,capital-loss=None}=>{native-country=United-States} is 0.9091
