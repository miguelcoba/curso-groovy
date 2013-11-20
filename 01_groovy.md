!SLIDE title-slide

# Groovy #

!SLIDE subsection 

# Getting started #

!SLIDE bullets incremental

# Environment #

* Groovy 1.7 requires JDK 1.5

!SLIDE smbullets

# Java setup #

* http://java.sun.com
* Add JAVA_HOME environment variable
* Add %JAVA_HOME%\bin to PATH

!SLIDE smbullets

# Groovy setup #

* http://groovy.codehaus.org/Download
* Unzip to C:\groovy
* Add GROOVY_HOME=C:\groovy
* Add %GROOVY_HOME%\bin to PATH

!SLIDE 

# Groovy programs #

    groovysh                  // Shell
    groovyConsole             // GUI
    groovy script.groovy      // Interpeter

!SLIDE 

# Groovy libs #

## Put them in %GROOVY_HOME%\lib

!SLIDE commandline incremental

# First Groovy program #

    $ groovy -e "println 'Hello, world!'"
    Hello, world!

!SLIDE subsection

# Language #

!SLIDE 

# Comments #

    @@@ ruby
    // until end of line
    /* between */
    /* with several
    lines */

!SLIDE 

# Strings #

    @@@ ruby
    'Single quotes'
    '''Single
    triple
    quotes'''
    "double quotes"
    """triple
    double
    quotes"""

!SLIDE 

# Printing #

    @@@ ruby 
    println "hello world!"  // hello world!
    print 'hello world!\n'  // hello world!
    println("hello world!") // hello world!
    println("hello" + " " + "world" + "!")
      // hello world!
    def a = 5
    println "a number: ${a}, and a sum: ${1 + 3}"
      // a number: 5, and a sum: 4

!SLIDE 

# Assignment #

    @@@ ruby 
    def a = 5
    def b = 6
    def c = 7, d = 8
    int e = 9
    String str = "10"
    def str2 = "11"

!SLIDE 

# Multiple assignment 1 #

    @@@ ruby 
    def (x,y) = [1, 2]
    println x   // 1
    println y   // 2

    def someFunction() {
      [ 1, 3, 5 ]
    }
    def (a, b, c) = someFunction()
    println "${a} ${b} ${c}"  // 1, 3, 5

!SLIDE 

# Multiple assignment 2 #

    @@@ ruby 
    def firstName, lastName

    (firstName, lastName) = "Miguel Cobá".tokenize()
    println firstName   // Miguel
    println lastName    // Cobá

    def (a,b,c) = [1,2]
    println "${a} ${b} ${c}" // 1 2 null
   
!SLIDE

# Parenthesis optional #

    @@@ ruby 
    println("Hello World!") // Hello World!
    println "Hello World!"  // Hello World!
  
!SLIDE

# Safe navigation #

    @@@ ruby 
    def str = null
    println str?.size() // null
    str = "abc"
    println str?.size() // 3

!SLIDE

# if-then-else #

    @@@ ruby 
    def a = 3
    if (a > 2) {
      println "was true"
    } else {
      println "was false"
    }

!SLIDE

# Loops #

    @@@ ruby 
    while( i > 0 ) {
      println i--  // post-decrement
    }

    10.times { println "hello" }

!SLIDE

# Reflection #

    @@@ ruby 
    def a = "string"       
    println a.class       // class java.lang.String
    println String.name   // java.lang.String
    println a.class.name  // java.lang.String
    println a.class.fields 
    println a.class.methods

!SLIDE

# Groovy booleans #

    @@@ ruby 
    ==
    !=
    >
    >=
    <
    <=

!SLIDE subsection

# Numbers #

!SLIDE bullets

# Integer #

* Integer
* Long
* BigInteger
* Short
* Byte

!SLIDE 

# Example #

    @@@ ruby
    [110, 300000000000, 1000000000000000000000]
      .each { println it.class }
    println '42'.toInteger()        // 42
    println Integer.parseInt("42")  // 42

!SLIDE bullets

# Decimal #

* Float
* Double
* BigDecimal

!SLIDE

# Examples #

    @@@ ruby
    [ 1.23e24, 4.56, 7.8E9, -1e-1]
      .each { println it.class }
    1.23e24.toString()
    (-5.24566e-1234).abs() // 5.24566E-1234

!SLIDE subsection

# Dates #

!SLIDE 

# Examples #

    @@@ ruby
    def today = new Date()
    def tomorrow = today + 1
    def yesterday = today - 1
    println today
    println tomorrow
    println yesterday
    println today.after(yesterday)
    
    def c1 = new GregorianCalendar(2010, 
                      Calendar.OCTOBER, 8)
    def c2 = new GregorianCalendar(2010,
                      Calendar.OCTOBER, 22)
    println c1.after(c2)  // false

!SLIDE subsection

# Collections #

!SLIDE

# Lists 1 #

    @@@ ruby
    def list = [1, 2, 3, 4]
    println list.get(2)         // 3
    println list[2]             // 3
    println list instanceof java.util.List  // true
    def empty = []
    println empty.size()        // 0
    empty.add(10)
    println empty.size()        // 1

!SLIDE

# Lists 2 #

    @@@ ruby
    def list = [ 1, 2 ,-4 , "hello", new Date()]
    println list.size()   // 5
    println list[0]       // 1
    println list.first()  // 1
    println list.last()   // Mon Jan 25 11:32:15 CDT 2010
    list << "new value"
    println list.last()   // new value
    def list2 = [ 1, 2, 3 ]
    list2 << [4, 5]
    println list2        // [1, 2, 3, [4, 5]]
    def list3 = list2.flatten()
    println list3.size() // 4
    println list3        // [1, 2, 3, 4, 5]
    
!SLIDE

# Operations 1 #

    @@@ ruby
    def items = ['one','two','three','four','five']
    items.findAll { it.size() > 3 }   
      // [ 'three', 'four', 'five' ]
    items.collect { it.capitalize() } 
      // ['One','Two','Three','Four','Five']
    items.each { println it } // prints each element
    items.eachWithIndex { v, i -> 
      println "${i}: ${v}"
    }

!SLIDE

# Operations 2 #

    http://groovy.codehaus.org/groovy-jdk
    - findIndexOf
    - grep
    - any
    - every
    - min
    - max
    - flatten
    - intersect
    - sort
    - join

!SLIDE

# Star operator #

    @@@ ruby
    ['one', 'two', 'three']*.size() // [3, 3, 5]

!SLIDE

# Examples #

    @@@ ruby
    def list = [1, 2, 2, 3]
    println list - [2]    // [1, 3]
    list.clear() 
    println list          // []
    list << 1
    list << 2
    println list.contains(2)  // true
    println list.count(1)     // 1
    list * 2                  // [1,2,1,2]
    list.indexOf(1)           // 0
    list.lastIndexOf(1)       // 2
    println list.reverse()    // [2, 1, 2, 1]
    list.removeAll(1)         // [2, 2]
    list.unique()             // [2]

!SLIDE subsection

# Array #

!SLIDE

# Examples #

    @@@ ruby
    def a = new Object[3]
    println a.size()  // 3
    println a.length  // 3
    a[0] = 'a'
    println a[0..1]   // ['a', null]

!SLIDE subsection

# Maps #

!SLIDE bullets

# Maps #

* keys/value store
* keys are strings by default
* use () to avoid conversion to string in keys

!SLIDE

# Examples 1 #

    @@@ ruby
    def a = new Object[3]
    def map = [ "first":1, 2:"number two", "3": 3.0]
    println map["first"]         // 1
    println map.first            // 1
    println map."2"              // null
    println map[2]               // number two
    println map[3]               // null
    println map["3"]             // 3.0
    println map."3"              // 3.0
    map.fourth = "new value"     
    println map.fourth           // new value
    println map.class            // null
    println map.getClass() // java.util.LinkedHashMap

!SLIDE

# Examples 2 #

    @@@ ruby
    def a = new Object[3]
    def map = [name: "Miguel",
              age: 31,
              date: new Date(),
              items: []]
    println map.get("name") // Miguel
    println map["name"]     // Miguel
    println map.name        // Miguel
    println map['items']    // []
    println map instanceof java.util.Map  // true

!SLIDE

# Examples 3 #

    @@@ ruby
    def a = new Object[3]
    def map = [:]
    println map.size()  // 0
    map.put("foo", 5)
    println map.size()  // 1
    println map.foo     // 5

!SLIDE

# Examples 4 #

    @@@ ruby
    def a = new Object[3]
    def a = 5   
    def map = [a:5, (a): 10]
    println map["a"]      // 5
    println map.a         // 5
    println map[5]        // 10
    println map[a]        // 10
    map.foo = "new value"
    println map.foo       // new value


!SLIDE subsection

# Ranges #

!SLIDE bullets

# Ranges details #

* java.lang.Comparable
* next()/previous()

!SLIDE 

# Inclusive ranges #

    @@@ ruby
    def a = new Object[3]
    def range = 5..8 
      // inclusive list: [5, 6, 7, 8]
    println range.size()    // 4
    println range.get(2)    // 7
    println range[2]        // 7
    println range instanceof java.util.List // true
    println range.contains(5)    // true
    println range.contains(8)    // true
    println range.from           // 5
    println range.to             // 8

!SLIDE

# Exclusive ranges #

    @@@ ruby
    def a = new Object[3]
    def range = 1..<4    // inclusive list: [1, 2, 3]
    println range.size()    // 3
    println range.get(2)    // 3
    println range[2]        // 3
    println range instanceof java.util.List    // true
    println range.contains(1)    // true
    println range.contains(4)    // false
    println range.from           // 1
    println range.to             // 3

!SLIDE

# Example 1 #

    @@@ ruby
    def a = new Object[3]
    def range = 'a'..'c'
    println range.size()      // 3
    println range[2]          // 'c'
    println range.from        // 'a'
    println range.to          // 'c'

!SLIDE

# Example 2 #

    @@@ ruby
    def a = new Object[3]
    for(i in 1..10) {
      println "Hello ${i}"
    }

    (1..10).each { println it }

    def var
    switch(age) {
      case 1..<18: var = "a"
      case 18..99: var = "b"
      default: var = "c"
    }

!SLIDE subsection

# String #

!SLIDE

# Delimited with " and ' #

    @@@ ruby
    def a = new Object[3]
    println "hello 'world'!"  // hello 'world'!
    println 'hello "world"!'  // hello "world"!

!SLIDE

# Concatenation #

    @@@ ruby
    def a = new Object[3]
    def a = "world!"
    println "hello" + world      // hello world!

!SLIDE

# Multi-line #

    @@@ ruby
    def a = new Object[3]
    def multiLineText = """hello\
    world\
    !
    """
    println multiLineText   // hello world!

!SLIDE bullets

# GString #

* $variable inside "-delimited strings
* ${expression} inside "-delimited strings

!SLIDE

# Example #

    @@@ ruby
    def a = new Object[3]
    def w = "world"
    println "hello ${w}!"           // hello world!
    println "hello $w!"             // hello world!
    println "today is: ${new Date()}"
      // today is: Sun Oct 17 22:50:02 CDT 2010

!SLIDE

# Examples #

    @@@ ruby
    def a = new Object[3]
    def str = "2010-10-22"
    def dateArray = str.split("-")
    def year = dateArray[0].toInteger()
    year = year + 1
    println (year + "-" + 
        dateArray[1] + "-" + 
        dateArray[2])
    println ([year, 
              dateArray[1], 
              dateArray[2]].join("-"))
    dateArray[0] = (dateArray[0].toInteger() + 1)
        .toString()
    println (dateArray.join("-"))
    println "Miguel".replace("igu","anu")

!SLIDE subsection

# Regular expressions #

!SLIDE

# regexp #

    ==~ matches patterns
    ==  matches equality
    //  delimiters for regexp

!SLIDE

# regexp 1 #

    @@@ ruby
    println "miguel" ==~ /miguel/
    println "miguel" ==~ /mi...l/
    println "miguel" ==~ /migu./
    println "pattern" ==~ /patterns?/
    println "patterns" ==~ /patterns?/
    println "miguel" ==~ /m(igu|anu)el/
    println "manuel" ==~ /m(igu|anu)el/
    println "mel" ==~ /m(igu|anu)?el/

!SLIDE

# regexp 2 #

    a?    0 or 1       


      - empty string or 'a'

!SLIDE

# regexp 2 #

    a*    0 or more    


      - empty string, 'a', 'aa', 'aaa', 'aaaa', etc

!SLIDE

# regexp 2 #

    a+    1 or more    


      - 'a', 'aa', 'aaa', etc

!SLIDE

# regexp 2 #

    a|b   a or b       


      - 'a' or 'b' but not both

!SLIDE

# regexp 2 #

    .     any single char 


      - 'a', 'x', '1', '+', etc

!SLIDE

# regexp 2 #

    [abcde]   any of a,b,c,d or e          


      - 'a','b','c','d','e'

!SLIDE

# regexp 2 #

    [1-3]    range, matches any of the char in the range   


      - '1', '2','3'

!SLIDE

# regexp 2 #

    [^123]   any except 1,2 or 3            


      - '4', 'r', '+'

!SLIDE

# regexp 2 #

    (abc)    group an expression            


      - 'abc'

!SLIDE

# regexp 2 #

    ^a       a at the beginning of line     


      - 'a'

!SLIDE

# regexp 2 #

    a$       a at the end of line           


      - 'a'

!SLIDE smaller

# regexp 3 #

## matcher =~

    @@@ ruby
    def a = new Object[3]
    def csv = "Coba, Miguel, 31, Groovy, Grails"
    def regexp = 
    /([a-zA-Z]+), ([a-zA-Z]+), ([0-9]+), ([a-zA-Z]+), ([a-zA-Z]+)/
    def matcher = (csv =~ regexp)
    if (matcher.matches()) {
      println(matcher.count)    // 1
      println(matcher[0])       
        // [Coba, Miguel, 31, Groovy, Grails]
      println(matcher[0][1])    // Cobá
      println(matcher[0][2])    // Miguel
      println(matcher[0][3])    // 31
      println(matcher[0][4])    // Groovy
      println(matcher[0][5])    // Grails
    }

## replacement

    @@@ ruby
    def str = "A string is always a string"
    def matcher = (str =~ /string/)
    str = matcher.replaceAll("number")
    println (str)

!SLIDE subsection

# Classes #

!SLIDE

# Examples #

    @@@ ruby
    class Counter {
      def num = 0
      def incr() { num++ }
      def decr() { num-- }
    }
    def c = new Counter()
    c.incr()
    println c.num             // 1
    1000.times { c.decr() }
    println c.num             // -999

!SLIDE subsection

# Closures #

!SLIDE

# Definition #
  
    Anonymous block of code that may
    - Take arguments
    - Return a value
    - Refrence and use variables declared in its 
      surrounding scope

!SLIDE

# Syntax #

    - { [arguments ->] statements }

    - [arguments ->]: optional comma-delimited list 
      of arguments, typed or untyped

    - statements: 0 or more groovy statements

!SLIDE subsection

# Closure Semantics #

!SLIDE

# Closures are anonymous #

      - Can be referenced using untyped variables 
        or typed variables of type Closure
      - Can be passed as method arguments and as 
        arguments to other closures

!SLIDE

# Implicit method #

      - Closures have one implicitly defined method, 
        the one described by the arguments and body
        of the closure.
      - Implicit method name is doCall()
      - It is invoked by the call() method or the () 
        syntax
    
!SLIDE

# Arguments 1 #

    - A closure has at least one argument, 
      available as the implicit parameter *it*
      IF NO EXPLICIT parameters are defined.

    - Explicit arguments can be typed or untyped. 
      When a parameter list is specified, the *it* 
      variable is not available

    - They are checked at runtime, not at compile 
      time

!SLIDE

# Arguments 2 #

    - If last argument is of type Object[], any 
      excess arguments at invocation time are placed 
      there

!SLIDE

# Example #

    @@@ ruby
    def msgSum = { text, Object[] args ->
      def sum = 0
      args.each { sum += it }
      text + sum
    }
    println msgSum("The sum is:", 1, 2)
    println msgSum("The sum is:", 1, 2, 4, 5)

!SLIDE

# Return value #

    Always return a value
    - one or more explicit return statements
    - value of the last executed statement if no 
      explicit return
    - if the last statement has no value, null is 
      returned

!SLIDE

# Example #

    @@@ ruby
    def currencyConverter = { rate, value ->
      rate * value
    }
    def usdMxnConverter = currencyConverter.curry(13)
    def eurMxnConverter = currencyConverter.curry(19)
    println usdMxnConverter(5) // 5 USD -> 65 MXN
    println eurMxnConverter(2) // 2 EUR -> 38 MXN
     
!SLIDE

# Examples 1 #

    @@@ ruby
    def pr = { println it }
    pr("hola mundo")      // hola mundo
    pr(2)                 // 2
    pr(new Date()) // Sun Oct 13 11:11:11 CDT 2010

!SLIDE

# Examples 2 #

    @@@ ruby
    def square = { it * it }
    println([1, 2, 3, 4].collect(square)) 
      // [1, 4, 9, 16]
    [1, 2, 3, 4].each(pr) // 1\n2\n3\n4\n

!SLIDE

# Examples 3 #

    @@@ ruby
    def aValue = 3
    def cl = { aValue * it }
    println cl(4)                 // 12
    println ([1, 2].collect(cl))  // [3, 6]

!SLIDE

# Examples 4 #

    @@@ ruby
    def cl = { param -> param + 4 }
    cl(6)     // 10
 
!SLIDE

# Examples 5 #

    @@@ ruby
    def cl = { p1, p2 -> p1 * p2 }
    println cl(3,4)         // 12
    println cl("hola", 3)   // holaholahola 

!SLIDE

# Examples 6 #

    @@@ ruby
    def l = [ 1, 2, 3, 4 ]
    def sum = 0
    l.each {
      sum += it
    }
    println "sum: ${sum}"

!SLIDE

# Examples 7 #

    @@@ ruby
    def myFile = new File("file.txt")
      // file.txt is in current directory
    printFileLine = { println "File line: " + it }
    myFile.eachLine( printFileLine )

!SLIDE subsection

# Groovy JDK #

!SLIDE 

# Groovy JDK #

## [http://groovy.codehaus.org/groovy-jdk/](http://groovy.codehaus.org/groovy-jdk/)

!SLIDE subsection

# SQL #

!SLIDE

# Simple query #

    @@@ ruby
    import groovy.sql.Sql
    def sql
    sql = Sql.newInstance(
            "jdbc:mysql://172.16.1.97/groovy",
            "groovy","groovy",
            "com.mysql.jdbc.Driver")
    sql.eachRow("select * from table", 
         {println "${it.id} ${it.aCol}"})

!SLIDE subsection

# Groovy technical details #

!SLIDE

# Default imports #

    @@@ ruby
    java.io.*
    java.lang.*
    java.math.BigDecimal
    java.math.BigInteger
    java.net.*
    java.util.*
    groovy.lang.*
    groovy.util.*

!SLIDE

# Assigment and equality #

    == equality operator
    = assignment operator
    is()

!SLIDE

# Reserved words #

     in

!SLIDE

# Arrays #

    @@@ ruby
    def int[] a = [1,2,3]

!SLIDE

# Optional elements #

    semicolon (;)
    return

!SLIDE

# Differences with Java #

## methods and classes are public by default


!SLIDE code smaller

# Exercise #

    @@@ ruby
    import groovy.sql.Sql
    
    def sql = Sql.newInstance(
      "jdbc:mysql://172.16.1.97/groovy",
      "groovy","groovy", 
      "com.mysql.jdbc.Driver")
    def myFile = new File("dump.txt")
    
    sql.eachRow("select * from tabla", { row ->
        def id = row.id ==~ /[0-9]/
        def email = row.email ==~ /.*@.*\..*/
        
        if(!id) { println "Bad id: ${row.id}" }
        if(!email) { println "Bad email: ${row.email}" }
        
        if (id && email) {
            def line = row.toRowResult().values().join('|')            
            println "Inserting ${line}" 
            myFile << line           
        } else {
            println "Bad record: ${row}"
        }      
    })

!SLIDE bullets

# Thanks #

* Miguel Cobá
* [miguel@trantaria.com](miguel@trantaria.com)

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/"><img alt="Licencia de Creative Commons" style="border-width:0" src="http://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" property="dct:title" rel="dct:type">Groovy Intro</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://trantaria.com" property="cc:attributionName" rel="cc:attributionURL">Miguel Cobá</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/">Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License</a>.
