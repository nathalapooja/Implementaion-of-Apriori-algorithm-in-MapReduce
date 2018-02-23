****Writing java files and text files
Copy all the source code files 
emacs Apriori.java
emacs AssociationRules.java
emacs ActionRules.java
emacs mammographic_attributes.txt
emacs mammmographic.data.txt
****check whether all the file are existing
ls
*** copy the mammographic data into hadoop file system
hadoop fs -put mamm*.txt 
**** we create a directory named apriori_classes
mkdir apriori_classes
*** Compile the codes 
javac -cp $(hadoop-classpath) apriori_classes/ build Xlint:none
*** Create a jar file 
jar -cvf Apriori.jar -C build/ .
*** copy to hadoop file system
hadoop fs -put Apriori.jar
*** Run the code using attirbute and data files
hadoop jar Apriori.jar apriori.group5.Apriori mammographic_attribute.txt mammographic_masses.data.txt ActionRulesOutput AssociationRulesOutput


scp path-TO-file username@dsba-hadoop.uncc.edu:~/
scp -r path_to_foder 