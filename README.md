# Extract text from any document
Uses Apache Tika library to parse documents automatically and extract text from them. 
It uses the `AutoDetectParser`(https://tika.apache.org/2.5.0/api/org/apache/tika/parser/AutoDetectParser.html) for 
detecting the format automatically before extracting text.

## JSAP
- Java Simple Argument Parser
- Accepts three arguments
- `--extract -i InputDirectory -o OutputDirectory`
- `--extract` JSAP boolean switch to initiate extraction of text
- `-i InputDirectory` JSAP option to set input directory/corpus containing the input files
- `-i OutputDirectory` JSAP option to set output directory to save extracted text files

## How to run
### Using the `Main` method
- in Windows, set arguments as `--extract -i H:\html-corpus -o H:\extracted-text`
- in Ubuntu, set arguments as `--extract -i /home/user/html-corpus -o /home/user/extracted-text`
### Using the exec-maven-plugin
- Include the Main method and the static arguments directly inside the plugin inside `pom.xml`

```xml

<plugin>
    <groupId>org.codehaus.mojo</groupId>
    <artifactId>exec-maven-plugin</artifactId>
    <version>3.1.0</version>
    <configuration>
        <mainClass>uk.ac.rothamsted.ide.textextractor.Main</mainClass>
        <arguments>
            <argument>--extract</argument>
            <argument>-i H:\html-corpus</argument>
            <argument>-o H:\text-from-html-corpus</argument>
        </arguments>
    </configuration>
</plugin>
```
- From the command line with dynamic arguments
```xml
<plugin>
   <groupId>org.codehaus.mojo</groupId>
   <artifactId>exec-maven-plugin</artifactId>
   <version>3.1.0</version>
</plugin>
```
- from terminal issue the command with arguments as follows (not working at this moment):
```shell
mvn exec:java -Dexec.mainClass=Main -Dexec.args="--extract -i H:\html-corpus -o H:\extracted-text"
```