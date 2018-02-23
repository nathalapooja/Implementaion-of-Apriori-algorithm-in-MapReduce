**** Group-5 ****
Here are the set of instructions to run part3 code
-----------------------------------------------------------------------------------------------------------
Download the zip file(this zip file will be stored in downloads)
Extract the zip file
Open command terminal
cd Downloads
cd Group5-Part3
Here we have the java files
-----------------------------------------------------------------------------------------------------------------
**** Create a build directory ****
mkdir -p build
------------------------------------------------------------------------------------------------------------------
**** Below Commands used to build and generate jar file ****
**Compilation using javac
javac -cp /usr/lib/hadoop/*:/usr/lib/hadoop-mapreduce/* /home/cloudera/Downloads/Group5-Part3/SourceCode/ActionRules.java /home/cloudera/Downloads/Group5-Part3/SourceCode/AssociationActionRules.java /home/cloudera/Downloads/Group5-Part3/SourceCode/Apriori.java -d build -Xlint:none
OR
javac -cp /usr/lib/hadoop/*:/usr/lib/hadoop-mapreduce/* *.java -d build -Xlint:none

** Jar Building
jar -cvf Apriori.jar -C build/ .
--------------------------------------------------------------------------------------------------------------------------
**** Store the input and jar files in hadoop file system ****
hadoop fs -put Car
hadoop fs -put Mammographic
hadoop fs -put Apriori.jar
// The above files will be stored into /user/cloudera
-----------------------------------------------------------------------------------------------------------------------------
*** Command to run Apriori jar ***
$hadoop jar <jar-file-name> <class-name> <attribute-file> <data-file> <action-rules-output> <association-action-rules-output>

*** Command to run Apriori jar for Mammographic data ***
hadoop jar Apriori.jar apriori.group5.Apriori Mammographic/mammographic_attribute.txt Mammographic/mammographic_masses.data.txt kddpart3/ActionRulesOutput kddpart3/AssociationRulesOutput

*** Command to run Apriori jar for Car data ***
hadoop jar Apriori.jar apriori.group5.Apriori Car/car.c45-names.attributes.txt Car/car.data.txt kddpart3/ActionRulesOutput kddpart3/AssociationRulesOutput
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
*** Commands to get output as text files ***
** Action Rules
hadoop fs -get kddpart3/ActionRulesOutput/part-r-00000  /home/cloudera/Desktop/M_ActionRulesOutput.txt
** Association ActionRules
hadoop fs -get kddpart3/AssociationRulesOutput/part-r-00000  /home/cloudera/Desktop/M_AssociationRulesOutput.txt

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
***Delete output folders before running algorithm again ***
hadoop fs -rm -r kddpart3/ActionRulesOutput
hadoop fs -rm -r kddpart3/AssociationRulesOutput

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

