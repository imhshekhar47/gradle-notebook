# Multimodule project with Gradle
We can create multimodule project efficiently with gradle.


## Project structure
Let setup a `multimodule-demo` project with two sub-modules `core` and `app` as shown below
```code
- /multimodule-demo               -- parent project
    |-- /core                     -- sub-module
    |-- /app                      -- sub-module
```

#### Create project structure
```bash
# create parent project 
mkdir multimodule-demo 
cd multimodule-demo \
    && gradle init --type kotlin-application --dsl kotlin \
    && cd -

# create core subproject
mkdir core \
    && cp build.gradle.kts core/build.gradle.kts 

# create app project
mkdir app \
    && cp build.gradle.kts app/build.gradle.kts

# clean the parent build file
echo "" > build.gradle.kts 
```

#### Configure `settings.gradle.kts`
This file contains the structure of the project. We need to include our newly created sub-modules `core` and `app` into the project structure.

```kotlin
rootProject.name = "multimodule-demo"

include(
    "core",
    "app"
)
```

#### Configure root project
Since `core` and `app` are sub modules of `multimodule-demo` parent project. We can apply all common build configurations from parent build script itself.

```kotlin
plugins {
    id("org.jetbrains.kotlin.jvm") version "1.3.50" apply false
    // add jvm plugin but do not apply
}

group = "gradle-multimodule-demo"
version = "0.1.0"

subprojects {
    // add common repositories for all subprojects
    repositories {
        mavenCentral()
    }

    // apply the common plugin for all subprojects
    apply(plugin = "org.jetbrains.kotlin.jvm")


    // apply the common dependencies for all subprojects
    dependencies {
        val implementation by configurations
        val testImplementation by configurations

        implementation(platform("org.jetbrains.kotlin:kotlin-bom"))
        implementation("org.jetbrains.kotlin:kotlin-stdlib-jdk8")

        testImplementation("org.jetbrains.kotlin:kotlin-test")
        testImplementation("org.jetbrains.kotlin:kotlin-test-junit")
    }
}
```

#### Configure submodules 

##### module: core
Since most of the configurations alrady defined in the root project. All we need to do here is to add additional dependencies which are required for this module.
```kotlin
dependencies {
    // relevant dependencies
}
```

##### module: app
Since this module is an application one, hence we need to add the `application` plugin.
```kotlin
plugins {
    application
}

dependencies {
    // add core module as dependency
    implementation(project(":core"))
}

application {
    mainClass = "org.hshekhar.AppKt"
}
```

The configuration is complete now. We can do the implmentation in each of the module as per our requirements. 

### Run
We can see tha
```bash
./gradlew clean build
./gradlew run 
```



## Repository
Example code is available [here](https://github.com/imhshekhar47/gradle-mutimodule-demo)
