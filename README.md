# Shell Primer
# Table of Contents
1. [Conditions and Loops](#conditions-and-loops)
2. [Files & Directories](#files--directories)
3. [Executing python script](#executing-python-script )

## Conditions and Loops
### If then else
```shell
var="XYZ"
if [[ $var="XYZ ]]; then
		echo " true "		
else
		echo " false "		
fi
```
### While loop
```shell
while true; do   
  echo "output something"
done 
```
## Files & Directories
### Copy contents of directory with subdirs to target directory
```shell
source_dir="/path/to/source/dir"
source_dir="/path/to/target/dir"
cp -rf $source_dir $target_dir
```
### Remove dir and its contents
```shell
source_dir="/path/to/source/dir"
rm -rf $source_dir
```
### get current working directory
```shell
cwd=${PWD##*/}
echo "current working directory is "$cwd
```
### check if directory exits
```shell
if [ -d "$dir_name" ]; then
		echo $dir_name" exists..."		
fi
```
### reading a file in while loop
```shell
while read line; do   
  echo $line
done < input_file.txt
```
## Executing python script 
```shell
argument1="arg_to_py_script"
python_command='python a_python_script.py '$argument1
output=$($python_command)		
echo "output of python script is"$output
```
## Piping output of curl to python 
```shell
output=$(curl -s "http:path_to_curl_service | python -c "exec(\"import json,sys; obj=json.load(sys.stdin); \\nif 'key' in obj.keys(): print(obj['key']); \\nelse: print(json.dumps(obj));\")")		
```
