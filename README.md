Linux server instruction
========================

#First part: Ubuntu

Ubuntu Installation
------------------

Package way
-----------

This is easy

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
        mkdir Path
        cd Path
        mkdir bin include lib share man etc
        cd
add path in ~/.zshrc

Custom way
----------

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
        mkdir Path
        cd Path
        mkdir bin include lib share man etc
        cd
add path in ~/.zshrc

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
        cd BuildFiles
        cd bin
        ln -s `pwd`/* ~/Developer/Path/bin/
        cd ../include
        ln -s `pwd`/* ~/Developer/Path/include/
        cd ../lib
        ln -s `pwd`/* ~/Developer/Path/lib/
        cd ../share
        ln -s `pwd`/* ~/Developer/Path/share/
        echo "python 2.7 complete"
        cd ~/Developer/ProgramFiles/python/Python-3.4.3
        mkdir BuildFiles
        ./configure --prefix=`pwd`/BuildFiles
        make
        make install
        cd BuildFiles
        cd bin
        ln -s `pwd`/* ~/Developer/Path/bin/
        # ln: failed to create symbolic link ‘/home/ubuntu/Developer/Path/bin/2to3’: File exists
        cd ../include
        ln -s `pwd`/* ~/Developer/Path/include/
        cd ../lib
        ln -s `pwd`/* ~/Developer/Path/lib/
        cd pkgconfig
        ln -s `pwd`/* ~/Developer/Path/lib/pkgconfig/
        cd ..
        cd ../share
        cd man/man1
        ln -s `pwd`/* ~/Developer/Path/share/man/man1/
        echo "python 3.4 complete"
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
        cd BuildFiles
        cd bin
        ln -s `pwd`/* ~/Developer/Path/bin/
        cd ../etc
        ln -s `pwd`/* ~/Developer/Path/etc/
        cd ../include
        ln -s `pwd`/* ~/Developer/Path/include/
        cd ../lib
        ln -s `pwd`/* ~/Developer/Path/lib/
        cd ../php
        mkdir ~/Developer/Path/php
        ln -s `pwd`/* ~/Developer/Path/php/
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
        cd BuildFiles
        cd bin
        ln -s `pwd`/* ~/Developer/Path/bin/
        cd ../include
        ln -s `pwd`/* ~/Developer/Path/include/
        cd ../lib
        ln -s `pwd`/* ~/Developer/Path/lib/
        cd pkgconfig
        ln -s `pwd`/* ~/Developer/Path/lib/pkgconfig/
        cd ..
        cd ../share
        ln -s `pwd`/* ~/Developer/Path/share/
        cd man/man1
        ln -s `pwd`/* ~/Developer/Path/share/man/man1/
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
        cd BuildFiles
        cd bin
        ln -s `pwd`/* ~/Developer/Path/bin/
        cd ../lib
        ln -s `pwd`/* ~/Developer/Path/lib/
        cd ../man
        ln -s `pwd`/* ~/Developer/Path/man/
        cd

###install [Lua](http://www.lua.org/download.html)
		sudo aptitude install libreadline-dev
        cd ~/Developer/ProgramFiles
        mkdir lua
        cd lua
        curl -R -O http://www.lua.org/ftp/lua-5.3.1.tar.gz
        tar zxf lua-5.3.1.tar.gz
        rm lua-5.3.1.tar.gz
        cd lua-5.3.1
        make linux test
        mkdir BuildFiles
add current BuildFiles path to Makefile install-top
		make linux install
		cd BuildFiles
		cd bin
        ln -s `pwd`/* ~/Developer/Path/bin/
        cd ../include
        ln -s `pwd`/* ~/Developer/Path/include/
        cd ../lib
        ln -s `pwd`/* ~/Developer/Path/lib/
        cd ../man
        cd man1
        ln -s `pwd`/* ~/Developer/Path/man/man1/
        cd ..
        cd ../share
        ln -s `pwd`/* ~/Developer/Path/share/
        cd
<!--
###install [mercurial](http://mercurial.selenic.com)
		cd ~/Developer/ProgramFiles
        mkdir mercurial
        cd mercurial
		wget http://mercurial.selenic.com/release/mercurial-3.5.tar.gz
		tar zxf mercurial-3.5.tar.gz
        rm mercurial-3.5.tar.gz
        cd mercurial-3.5
        mkdir BuildFiles
        make PREFIX=`pwd`/BuildFiles install
-->

###install [vim](https://github.com/vim/vim)
		sudo aptitude install libncurses5-dev libgnome2-dev libgnomeui-dev libgtk2.0-dev libatk1.0-dev libbonoboui2-dev libcairo2-dev libx11-dev libxpm-dev libxt-dev python-dev ruby-dev mercurial
        cd ~/Developer/ProgramFiles
        mkdir vim
        cd vim
        git clone https://github.com/vim/vim
        mv vim vim-7.4.843
        cd vim-7.4.843
        mkdir BuildFiles
        cd src
        ./configure --with-features=huge --enable-multibyte --enable-rubyinterp --enable-pythoninterp --with-python-config-dir=/home/ubuntu/Developer/ProgramFiles/python/Python-2.7.10/BuildFiles/lib/python2.7/config  --enable-python3interp --with-python3-config-dir=python/Python-3.4.3/BuildFiles/lib/python3.4/config-3.4m --enable-perlinterp --enable-luainterp --enable-gui=gtk2 --enable-cscope --prefix=/home/ubuntu/Developer/ProgramFiles/vim/vim-7.4.843/BuildFiles

###install zsh and [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)
        sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" 
        sudo aptitude install zsh
        chsh -s /bin/zsh
        echo "In gnome-terminal, select profile preference.\n\nMake sure you're editing the 'default' profile, and go to the "Title and Command" tab.\n\nUnder "Command" there are three checkboxes: "Run command as a login shell", "Update login records when command is launched", and "Run a custom command instead of my shell".\n\nI checked all three boxes, and under "Custom command:" I put zsh.\n\nClose the terminal and restart the terminal."

