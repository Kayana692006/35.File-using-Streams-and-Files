# 35.File-using-Streams-and-Files
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.List;
import java.util.stream.Collectors;
public class SimpleStreamAndFileExample {
public static void main(String[] args) {
// Define file paths
String inputFilePath = &quot;input_names.txt&quot;;
String outputFilePath = &quot;output_uppercase.txt&quot;;
try {
// Read names from the input file using BufferedReader and Java streams
List&lt;String&gt; names = readNamesFromFile(inputFilePath);
// Convert names to uppercase using Java streams
List&lt;String&gt; uppercaseNames = names.stream()
.map(String::toUpperCase)
.collect(Collectors.toList());
// Write uppercase names to the output file using BufferedWriter
writeUppercaseNamesToFile(outputFilePath, uppercaseNames);
System.out.println(&quot;Uppercase names written to &quot; + outputFilePath);
} catch (IOException e) {

e.printStackTrace();
}
}
// Read names from a file using BufferedReader and Java streams
private static List&lt;String&gt; readNamesFromFile(String filePath) throws IOException {
try (BufferedReader reader = new BufferedReader(new FileReader(filePath))) {
return reader.lines().collect(Collectors.toList());
}
}
// Write uppercase names to a file using BufferedWriter
private static void writeUppercaseNamesToFile(String filePath, List&lt;String&gt;
uppercaseNames) throws IOException {
try (BufferedWriter writer = new BufferedWriter(new FileWriter(filePath))) {
for (String name : uppercaseNames) {
writer.write(name);
writer.newLine();
}
}
}
}
OUTPUT
ALICE
BOB
CHARLIE
DAVID
EVE
