# Gradle tutorial
Gradle is an open-source build automation tool that is designed to be flexible enough to build almost any type of software.

## Setup
```bash
# Download
curl https://downloads.gradle-dn.com/distributions/gradle-5.6.4-bin.zip --output gradle-5.6.4-bin.zip

# Unzip
unzip gradle-5.6.4-bin.zip

# Move to installation directory
mv gradle-5.6.4 /c/Installation/

# setup path
export GRADLE_HOME=/c/Installation/gradle-5.6.4
export PATH=${PATH}:${GRADLE_HOME}/bin

# Check installation
gradle -v
```


## Usage
```bash
gradle init
```

## References
  
[Gradle Project Initializer](https://gradle-initializr.cleverapps.io/)
[DSL Reference](https://docs.gradle.org/5.6.4/dsl/)

#### Downloads
[Releases](https://gradle.org/releases/)