Linux server instruction
========================

#First part: Ubuntu

Ubuntu Installation
------------------

This is easy

Build the Ubuntu server
----------------------

###install aptitude
        sudo apt-get update
        sudo apt-get install aptitude
        sudo aptitude update
        sudo aptitude upgrade

###install git
        sudo aptitude install git

###create developer folders
        cd
        mkdir Developer
        cd Developer
        mkdir ProgramFiles
        mkdir Projects
        mkdir bin

###install [python](https://www.python.org/downloads/source/)
        sudo aptitude install libssl-dev openssl
        cd ~/Developer/ProgramFiles
        mkdir python
        cd python
        wget https://www.python.org/ftp/python/2.7.10/Python-2.7.10.tgz
        wget https://www.python.org/ftp/python/3.4.3/Python-3.4.3.tgz
        echo "Decompress these packages"
        tar -xzf Python-2.7.10.tgz
        tar -xzf Python-3.4.3.tgz
        rm Python-2.7.10.tgz Python-3.4.3.tgz
        cd Python-2.7.10
        mkdir BuildFiles
        ./configure --prefix=`pwd`/BuildFiles
        make
        make install
        cd BuildFiles/bin
        ln -s `pwd`/python2.7 ../../../../../bin/python2.7
        cd ~/Developer/bin
        sudo ln -s `pwd`/python2.7 /usr/local/bin/python2.7
        echo "python 2.7 complete"
        cd ~/Developer/ProgramFiles/python/Python-3.4.3
        mkdir BuildFiles
        ./configure --prefix=`pwd`/BuildFiles
        make
        make install
        cd BuildFiles/bin
        ln -s `pwd`/python3.4 ../../../../../bin/python3.4
        sudo ln -s `pwd`/python3.4 /usr/local/bin/python3.4
        echo "python 3.4 complete"
        cd ~/Developer/bin
        ln -s python2.7 ./python
        sudo ln -s `pwd`/python /usr/local/bin/python
        cd

###install [php](https://secure.php.net/downloads.php)
        sudo aptitude install libxml2-dev
        cd ~/Developer/ProgramFiles
        mkdir php
        cd php
        wget https://secure.php.net/distributions/php-5.6.12.tar.gz
        tar -xzf php-5.6.12.tar.gz
        rm php-5.6.12.tar.gz
        cd php-5.6.12
        mkdir BuildFiles
        ./configure --prefix=`pwd`/BuildFiles
        make
        make install
        cd BuildFiles/bin
        ln -s `pwd`/php ../../../../../bin/php
        cd ~/Developer/bin
        sudo ln -s `pwd`/php /usr/local/bin/php
        cd

###install [ruby](https://www.ruby-lang.org/en/downloads/)
        cd ~/Developer/ProgramFiles
        mkdir ruby
        cd ruby
        wget https://cache.ruby-lang.org/pub/ruby/2.2/ruby-2.2.3.tar.gz
        tar -xzf ruby-2.2.3.tar.gz
        rm ruby-2.2.3.tar.gz
        cd ruby-2.2.3
        mkdir BuildFiles
        ./configure --prefix=`pwd`/BuildFiles
        make
        make install
        cd BuildFiles/bin
        ln -s `pwd`/ruby ../../../../../bin/ruby
        cd ~/Developer/bin
        sudo ln -s `pwd`/ruby /usr/local/bin/ruby
        cd

###install [perl](http://www.cpan.org/src/README.html)
        cd ~/Developer/ProgramFiles
        mkdir perl
        cd perl
        wget http://www.cpan.org/src/5.0/perl-5.22.0.tar.gz
        tar -xzf perl-5.22.0.tar.gz
        rm perl-5.22.0.tar.gz
        cd perl-5.22.0
        mkdir BuildFiles
        ./Configure -des -Dprefix=`pwd`/BuildFiles
        make
        make test
        make install
        cd BuildFiles/bin
        ln -s `pwd`/perl ../../../../../bin/perl
        cd ~/Developer/bin
        sudo ln -s `pwd`/perl /usr/local/bin/perl
        cd

###install [Lua](http://www.lua.org/download.html)
        cd ~/Developer/ProgramFiles
        mkdir lua
        cd lua
        curl -R -O http://www.lua.org/ftp/lua-5.3.1.tar.gz
        tar zxf lua-5.3.1.tar.gz
        rm lua-5.3.1.tar.gz
        cd lua-5.3.1
        make linux test

###install [vim](https://github.com/vim/vim)
        cd ~/Developer/ProgramFiles
        git clone https://github.com/vim/vim
        cd vim/src

###install zsh and [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)
        sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" 
        sudo aptitude install zsh
        chsh -s /bin/zsh
        echo "In gnome-terminal, select profile preference.\n\nMake sure you're editing the 'default' profile, and go to the "Title and Command" tab.\n\nUnder "Command" there are three checkboxes: "Run command as a login shell", "Update login records when command is launched", and "Run a custom command instead of my shell".\n\nI checked all three boxes, and under "Custom command:" I put zsh.\n\nClose the terminal and restart the terminal."

