# TestNG

This is collection about using **TestNG** version 7.4.0.

## Requirements
The following software are needed for using TestNG version 7.4.0
1. TestNG 7.4.0 from https://mvnrepository.com/artifact/org.testng/testng/7.4.0

2. JCommander 1.78 from https://mvnrepository.com/artifact/com.beust/jcommander/1.78
3. JQuery 3.51 from https://mvnrepository.com/artifact/org.webjars/jquery/3.5.1

Place these 3 files in a Java library directory, e.g. `lib`.

## Command Line Usage

### Compiling test cases

```bash
javac -cp .:directory-containing-testng TestFileName.java
```

### Executing test cases

There are several ways to execute test cases

#### Direct execution

```bash
java -cp .:directory-containing-testng org.testng.TestNG -testclass TestFileName
```

#### Use xml file

```bash
java -cp .:directory-containing-testng org.testng.TestNG testng.xml
```

#### Use ant

```bash
ant
```
