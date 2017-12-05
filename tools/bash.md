A great tutorial is here: http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc3


#### String length  
    ${#test}
    
#### Comparison
    -eq 等于,如:if [ "$a" -eq "$b" ]   
    -ne 不等于,如:if [ "$a" -ne "$b" ]   
    -gt 大于,如:if [ "$a" -gt "$b" ]   
    -ge 大于等于,如:if [ "$a" -ge "$b" ]   
    -lt 小于,如:if [ "$a" -lt "$b" ]   
    -le 小于等于,如:if [ "$a" -le "$b" ]   
    <   小于(需要双括号),如:(("$a" < "$b"))   
    <=  小于等于(需要双括号),如:(("$a" <= "$b"))   
    >   大于(需要双括号),如:(("$a" > "$b"))   
    >=  大于等于(需要双括号),如:(("$a" >= "$b"))  
    
    For strings comparsion, follow this way: 
    if [ "$test"x = "test"x ]; then
    That can prevent errors when your input is empty ("x" = "testx")

#### Change line
    echo -en '\n'
    
##### exit
    exit 1
    
##### Error messages catching
    var=$(git status 2>&1)
    In this way, you redirect stderr to stdout and then capture the output.
    Otherwise when for error messages are written on stderr and your command: var=$(git status) is only capturing stdout.
    
    stdout to a file
    ls -l > ls-l.txt
    
    stderr to a file
    grep da * 2> grep-errors.txt
    
    stdout to stderr
    grep da * 1>&2 
    
    stderr to stdout
    grep * 2>&1
    
    stderr and stdout to a file
    rm -f $(find / -name core) &> /dev/null 
    
#####
