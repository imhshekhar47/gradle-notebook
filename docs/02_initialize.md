# initializing a gradle project
Gradle can create project from scratch and it comes with the cli based commands to initialize projects of various types such as
- basic
- java-application
- java-library
- scala-application
- scala-library
- kotlin-application
- kotlin-library
- groovy-application
- groovy-llibrary

## Setup project directory
```bash
mkdir gradle-demo 
cd gradle-demo
```

## Initialize the project
```bash
gradle init
```
Gradle init then prompts for various config details as shown below and the nitializes the project with selected configurations
```code
Select type of project to generate:
  1: basic
  2: application
  3: library
  4: Gradle plugin
Enter selection (default: basic) [1..4] 2

Select implementation language:
  1: C++
  2: Groovy
  3: Java
  4: Kotlin
  5: Swift
Enter selection (default: Java) [1..5] 4

Select build script DSL:
  1: Groovy
  2: Kotlin
Enter selection (default: Kotlin) [1..2] 2

Project name (default: app): gradle-demo
Source package (default: gradle.demo): org.hshekhar

BUILD SUCCESSFUL in 1m 2s
2 actionable tasks: 2 execute
```

### Project Anatomy 
This generates the below file structure
```code
/gradle-demo                                    -- project directory
  |-- /.gradle                                  -- gradle build tracker    
  |-- /gradle                                   -- 
  |      |-- /wrapper                           -- gradle build wrapper 
  |             |-- gradle-wrapper.jar          -- 
  |             |-- gradle-wrapper.properties   -- 
  |-- /src                                      -- source 
  |      |-- /main                              -- application code 
  |      |      |-- /kotlin                     -- 
  |      |      |-- /resources                  -- 
  |      |-- /test                              -- test code  
  |             |-- /kotlin                     -- 
  |             |-- /resources                  -- 
  |-- build.gradle.kts                          -- gradle build file
  |-- settings.gradle.kts                       -- settings for gradle build
  |-- gradlew                                   -- wrapper script (Unix) 
  |-- gradlew.bat                               -- wrapper script (Windows)
```
## Gradle Tasks

#### tasks
We can see the gradle tasks already configured for this project during initialization
```bash
./gradlew tasks
# shows all the task configured in this project
```

#### clean and build
```bash
./gradlew clean build
# clean and builds the source code (/build) 
```

#### test
```bash
./gradlew test
# runs the test from /gradle-demo/src/test
```

## Gradle properties
```bash
./gradlew properties
```
This show extensive list of properties configured for this project. A few of them are listed below
```code
> Task :properties

------------------------------------------------------------
Root project
------------------------------------------------------------

applicationName: gradle-demo
buildDir: C:\projects\github\gradle-tutorial\app\build
buildFile: C:\projects\github\gradle-tutorial\app\build.gradle.kts
childProjects: {}
description: null
group:
name: gradle-demo
project: root project 'gradle-demo'
rootDir: C:\projects\github\gradle-tutorial\app
rootProject: root project 'gradle-demo'
version:

BUILD SUCCESSFUL in 3s
1 actionable task: 1 executed
```
we can change many of these properties. Lets add following lines to `build.gradel.kts` file, 
```kotlin
description = "Demo project"
group = "org.hshekhar"
version = "1.0"
```
and re-execute `gradle properties` we can see that the properties now updated. 


## References
[Gradle Project Initializer](https://gradle-initializr.cleverapps.io/)