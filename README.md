# CS 102 Project for 2019-2020 Spring Semester in Bilkent

## Design and Style Guidelines
1. In this project we strictly follow certain rules which are gathered together by David Davenport:
   - design and implementation rules which can be found  [here](https://web.archive.org/web/20170930094137/http://www.cs.bilkent.edu.tr/~david/cs101/practicalwork/2010/JavaLabs.htm),
   - and we have rules on OOP [here](https://web.archive.org/web/20170930110056/http://www.cs.bilkent.edu.tr/~david/cs101/practicalwork/2010/JavaOOPLabs.htm),
   - and of course a strict style guide lines [here](https://web.archive.org/web/20170930110102/http://www.cs.bilkent.edu.tr/~david/cs101/practicalwork/2010/styleguidelines.htm).


## About javadoc comments
Use of javadoc comments just before classes, constructors and methods is **mandatory**.
1. Examples of styling
   * Before Classes
   ```
   /**
    * This class (or object) have blah blah blah and can do blah blah blah
    * @author Muhammed Can Küçükaslan
    * @version 2020.02.14 
    */
    public class Example {
    ...
    }
   ```
   
   * Before constructors
    ```
    /**
    * This generates a ClassName object and sets default or given (by parameters) values to the properties
    * @param paramName is blah blah blah
    */
   public ClassName( Object paramName) {
   ...
   }
    ```
   * Before Methods
    ```
    /**
    *  This method does blah blah blah
    * (if an instance method) changes blah blah properties in blah blah way
    *  @return a logical value which is ObjectType (or a primitive value)
    */
   public ObjectType getName()
   {
   ...
   }
   ```
