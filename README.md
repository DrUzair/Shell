# Shell Primer
1. [Creating Shell Script](#creating-shell-script)
2. [Conditions and Loops](#conditions-and-loops)
3. [Files & Directories](#files--directories)
4. [Executing python script](#executing-python-from-shell)
5. [Regular Expressions](#regular-expressions)
## Creating Shell Script
### Test script
Save following in a file with sh extension e.g. shell_script.sh 
```shell
#!/bin/sh
echo "hello from shell"
```
and give permissions
```shell
chmod 777 -R shell_script.sh
```
execute
```shell
sh shell_script.sh
```
```shell
#!/bin/sh
arg=$1
echo "hello from shell"
echo "argument "$arg" recieved"
```
execute
```shell
sh shell_script.sh argument_value
```

### Passing arguments to script

## Conditions and Loops
### If then else
Equality **=**check
```shell
#!/bin/sh
var="XYZ"
if [[ $var="XYZ ]]; then
		echo " true "		
else
		echo " false "		
fi
```
Non-equality **=~** check
```shell
#!/bin/sh
var="XYZ"
if [[ $var=~"XYZ ]]; then
		echo " true "		
else
		echo " false "		
fi
```

### While loop
```shell
#!/bin/sh
while true; do   
  echo "output something"
done 
```
## Files & Directories
### Copy contents of directory with subdirs to target directory
```shell
#!/bin/sh
source_dir="/path/to/source/dir"
source_dir="/path/to/target/dir"
cp -rf $source_dir $target_dir
```
### Remove dir and its contents
```shell
#!/bin/sh
source_dir="/path/to/source/dir"
rm -rf $source_dir
```
removing named files and directories from cwd
```shell
#!/bin/sh
source_dir="/path/to/source/dir"
cd $source_dir
rm -rf sub_dir1/ sub_dir2/ sub_dir3/sub_sub_dir1/*.csv
```
### get current working directory
```shell
#!/bin/sh
cwd=${PWD##*/}
echo "current working directory is "$cwd
```
### check if directory exits
```shell
#!/bin/sh
if [ -d "$dir_name" ]; then
		echo $dir_name" exists..."		
fi
```
### Get directory name 
```shell
#!/bin/sh
parent_dir=$( dirname $file_path)
echo "The "$file_path" is in "$parent_dir"
```
### reading a file in while loop
```shell
#!/bin/sh
while read line; do   
  echo $line
done < input_file.txt
```
### Reading a csv file
Consider reading a csv file (example_file.csv) from current directory. example_file.csv has two columns.
The cat (short for concatenate) is used to read the file and pipe into while loop row by row.
```shell
#!/bin/sh
cat example_file.csv | while read col1 col1; do 
  echo "col1 value : "$col1", col2 value : "$col2
done
```
### Writing to a csv file
Consider writing to a csv file (example_file.csv) placed in current directory. example_file.csv has two columns.
The cat (short for concatenate) is used to read the file and pipe into while loop row by row.
```shell
#!/bin/sh
col1="val1"
col2="val2"
echo "$col1, $col2" >> example_file.csv
```
## Executing python from shell
### Python Script with arguments
```shell
#!/bin/sh
argument1="arg_to_py_script"
python_command='python a_python_script.py '$argument1
output=$($python_command)		
echo "output of python script is"$output
```
### Piping output of curl to python 
```shell
#!/bin/sh
output=$(curl -s "http:path_to_curl_service | python -c "exec(\"import json,sys; obj=json.load(sys.stdin); \\nif 'key' in obj.keys(): print(obj['key']); \\nelse: print(json.dumps(obj));\")")		
```
## Regular Expressions
### Check if the variable value is a number
```shell
var=1
re='^[0-9]+$'
if ! [[ $var =~ $re ]] ; then
   echo "the value is "$var    
else
   echo "the value "$var" is not a number"    
fi
```
