# Difference between contraints based alignment and nebula plugin alignment

# Nebula plugin based dependencies output

`cd nebulaPlugin`
`./gradlew dependencies --configuration runtimeClasspath`

```
runtimeClasspath - Runtime classpath of source set 'main'.
+--- com.fasterxml.jackson.core:jackson-core:2.9.4
+--- com.fasterxml.jackson.core:jackson-databind:2.7.9 -> 2.9.4
|    +--- com.fasterxml.jackson.core:jackson-annotations:2.9.0 -> 2.9.4
|    \--- com.fasterxml.jackson.core:jackson-core:2.9.4
\--- com.fasterxml.jackson.module:jackson-module-kotlin:2.9.4.1
     +--- com.fasterxml.jackson.core:jackson-databind:2.9.4 (*)
     +--- com.fasterxml.jackson.core:jackson-annotations:2.9.0 -> 2.9.4
     \--- org.jetbrains.kotlin:kotlin-reflect:1.2.21
          \--- org.jetbrains.kotlin:kotlin-stdlib:1.2.21
               \--- org.jetbrains:annotations:13.0
```

# Gradle dependency contrain based alignment

`cd gradleCore`
`./gradlew dependencies --configuration runtimeClasspath`

```
runtimeClasspath - Runtime classpath of source set 'main'.
+--- com.fasterxml.jackson.core:jackson-core:2.9.4
|    +--- com.fasterxml.jackson.core:jackson-annotations:(,2.9.4] -> 2.9.0
|    |    +--- com.fasterxml.jackson.core:jackson-core:(,2.9.0] -> 2.9.4 (*)
|    |    +--- com.fasterxml.jackson.core:jackson-databind:(,2.9.0] -> 2.9.4
|    |    |    +--- com.fasterxml.jackson.core:jackson-annotations:2.9.0 (*)
|    |    |    +--- com.fasterxml.jackson.core:jackson-core:2.9.4 (*)
|    |    |    +--- com.fasterxml.jackson.core:jackson-annotations:(,2.9.4] -> 2.9.0 (*)
|    |    |    +--- com.fasterxml.jackson.core:jackson-core:(,2.9.4] -> 2.9.4 (*)
|    |    |    \--- com.fasterxml.jackson.module:jackson-module-kotlin:(,2.9.4] -> 2.9.4.1
|    |    |         +--- com.fasterxml.jackson.core:jackson-databind:2.9.4 (*)
|    |    |         +--- com.fasterxml.jackson.core:jackson-annotations:2.9.0 (*)
|    |    |         +--- org.jetbrains.kotlin:kotlin-reflect:1.2.21
|    |    |         |    \--- org.jetbrains.kotlin:kotlin-stdlib:1.2.21
|    |    |         |         \--- org.jetbrains:annotations:13.0
|    |    |         +--- com.fasterxml.jackson.core:jackson-annotations:(,2.9.4.1] -> 2.9.0 (*)
|    |    |         +--- com.fasterxml.jackson.core:jackson-core:(,2.9.4.1] -> 2.9.4 (*)
|    |    |         \--- com.fasterxml.jackson.core:jackson-databind:(,2.9.4.1] -> 2.9.4 (*)
|    |    \--- com.fasterxml.jackson.module:jackson-module-kotlin:(,2.9.0] -> 2.9.4.1 (*)
|    +--- com.fasterxml.jackson.core:jackson-databind:(,2.9.4] -> 2.9.4 (*)
|    \--- com.fasterxml.jackson.module:jackson-module-kotlin:(,2.9.4] -> 2.9.4.1 (*)
+--- com.fasterxml.jackson.core:jackson-databind:2.7.9 -> 2.9.4 (*)
\--- com.fasterxml.jackson.module:jackson-module-kotlin:2.9.4.1 (*)
```

com.fasterxml.jackson.core:jackson-annotations is being resolved to 2.9.0 instead of 2.9.4
