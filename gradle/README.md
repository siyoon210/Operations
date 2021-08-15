## gradle

### (21.8.15) 의존성 포함하여 jar 파일 만들기
```
task buildJar(type: Jar) {
    baseName('base-name')
    version("0.0.1")
    manifest {
        attributes(
                'Main-Class': "main-class-name"
        )
    }
    from {
        configurations.runtimeClasspath.collect { it.isDirectory() ? it : zipTree(it) }
    }
    with jar
}
```
