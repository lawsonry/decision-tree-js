Decision Tree JS
================

Small JavaScript implementation of algorithm for training [Decision Tree](http://en.wikipedia.org/wiki/Decision_tree) and [Random Forest](http://en.wikipedia.org/wiki/Random_forest) classifiers.

This project is made possible by the ID3 implementation efforts of lagodiuk (whom I've forked this project from). 

### Purpose ###

This project extends the original decision tree generation algorithm by providing a results-oriented forecasting prediction model. Data is inputted by hand as a method of the cleaning/preparation component of the data mining workflow and then processed with extra elements on top of simple prediction. 

### Methodology ###

A set of student data `S1` is given to the model as training data. Follow-on data in a set `S2` is presented and then predictions of `S2` are created from the trained model using `S1`. Individual predictions are made and then an aggregate model accuracy is provided. (under construction)

###Example of usage###
Predicting sex of characters from 'The Simpsons' cartoon, using such features as weight, hair length and age

Online demo: http://jsfiddle.net/xur98/
```javascript
// Training set
var data = 
    [{person: 'Homer', hairLength: 0, weight: 250, age: 36, sex: 'male'},
     {person: 'Marge', hairLength: 10, weight: 150, age: 34, sex: 'female'},
     {person: 'Bart', hairLength: 2, weight: 90, age: 10, sex: 'male'},
     {person: 'Lisa', hairLength: 6, weight: 78, age: 8, sex: 'female'},
     {person: 'Maggie', hairLength: 4, weight: 20, age: 1, sex: 'female'},
     {person: 'Abe', hairLength: 1, weight: 170, age: 70, sex: 'male'},
     {person: 'Selma', hairLength: 8, weight: 160, age: 41, sex: 'female'},
     {person: 'Otto', hairLength: 10, weight: 180, age: 38, sex: 'male'},
     {person: 'Krusty', hairLength: 6, weight: 200, age: 45, sex: 'male'}];

// Configuration
var config = {
    trainingSet: data, 
    categoryAttr: 'sex', 
    ignoredAttributes: ['person']
};

// Building Decision Tree
var decisionTree = new dt.DecisionTree(config);

// Building Random Forest
var numberOfTrees = 3;
var randomForest = new dt.RandomForest(config, numberOfTrees);

// Testing Decision Tree and Random Forest
var comic = {person: 'Comic guy', hairLength: 8, weight: 290, age: 38};

var decisionTreePrediction = decisionTree.predict(comic);
var randomForestPrediction = randomForest.predict(comic);
```
Data taken from presentation: http://www.cs.sjsu.edu/faculty/lee/cs157b/ID3-AllanNeymark.ppt
