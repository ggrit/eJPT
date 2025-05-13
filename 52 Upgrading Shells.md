# 52 Upgrading Shells

# Upgrading Non-Interactive Shells 

### DEMO

```shell
cat /etc/shell # Available shells
/bin/bash -i 

# With Python 
python --version # It's installed?
python -c 'import pty; pty.spawn("/bin/bash")'

# With Perl 
perl --help # It's installed? 
# perl -e 'exec' "/bin/bash";'

# With Ruby
ruby: exec "/bin/bash"

# Setting up env variables
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
# Upgrades... 
export TERM=xterm
export SHELL=bash
```

#cybersecurity #eJPT 