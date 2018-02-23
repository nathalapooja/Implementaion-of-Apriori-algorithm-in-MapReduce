Word Count 1:

mkdir wordcount_classes
javac WordCount.java -cp $(hadoop classpath) -d wordcount_classes/
jar -cvf wordcount.jar -C wordcount_classes/ .
hdfs dfs -mkdir -p usr/pni1/wordcount/input1
hdfs dfs -copyFromLocal 03_MammalsBook_Text_34848.txt.utf8.txt usr/pni1/wordcount/input1
hadoop jar wordcount.jar org.myorg.WordCount usr/pni1/wordcount/input1 usr/pni1/wordcount/output1
hdfs dfs -copyToLocal usr/pni1/wordcount/output1 WordCountV1Output



Word Count 2:
mkdir wordcount_classes
javac WordCount.java -cp $(hadoop classpath) -d wordcount_classes/
jar -cvf wordcount.jar -C wordcount_classes/ .

hdfs dfs -mkdir -p usr/pni1/wordcount/input2
hdfs dfs -copyFromLocal 03_MammalsBook_Text_34848.txt.utf8.txt usr/pni1/wordcount/input2
hadoop jar wordcount.jar org.myorg.WordCount -Dwordcount.case.sensitive=true usr/pni1/wordcount/input2 usr/pni1/wordcount/output2 -skip usr/pni1/wordcount/patterns.txt
hdfs dfs -copyToLocal usr/pni1/wordcount/output2 WordCountV2Output
