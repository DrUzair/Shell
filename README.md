# Shell Primer
# Table of Contents
1. [Creating Shell Script](#creating-shell-Script)
2. [Conditions and Loops](#conditions-and-loops)
3. [Files & Directories](#files--directories)
4. [Executing python script](#executing-python-from-shell)

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
```shell
#!/bin/sh
var="XYZ"
if [[ $var="XYZ ]]; then
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
### reading a file in while loop
```shell
#!/bin/sh
while read line; do   
  echo $line
done < input_file.txt
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
