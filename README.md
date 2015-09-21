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

###install ssh
        sudo aptitude install openssh-server openssh-client
Use ifconfig to check the ip address

###create developer folders
        cd
        mkdir Developer
        cd Developer
        mkdir ProgramFiles
        mkdir Projects
        mkdir Path
        mkdir Temp
        cd Path
        mkdir bin include lib share man etc
        cd
add path in ~/.zshrc or /etc/profile.d/system_wide_path.sh and restart

###install for vmware tools
        sudo aptitude install gcc make build-essential
        sudo mkdir /mnt/cdrom
        sudo mount /dev/cdrom /mnt/cdrom
        cp -r /mnt/cdrom ~/Developer/Temp
        sudo chmod -R 775 ~/Developer/Temp
        cd ~/Developer/Temp
        tar xzvf VMwareTools-x.x.x-xxxx.tar.gz
        cd vmware-tools-distrib
        sudo ./vmware-install.pl
        sudo shutdown -r now

###install git
        sudo aptitude install git

###install things
        sudo locale-gen zh_CN.UTF-8
        sudo aptitude install vim python-dev ruby-dev python3-dev php5-dev perl lua5.2

###[vim preference](https://github.com/peidong/vimrc)
        sudo aptitude install exuberant-ctags ack-grep git build-essential cmake python-dev
        cd ~
        git clone https://github.com/peidong/vimrc.git
        mv vimrc .vim
        ln -s ~/.vim/vimrc ~/.vimrc
        ln -s ~/.vim/ycm_extra_conf.py ~/.ycm_extra_conf.py
        git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim
Then vim, and :PluginInstall

        cd ~/.vim/bundle/YouCompleteMe
        ./install.py --clang-completer --omnisharp-completer --gocode-completer
        mkdir ~/.undo_history/

###install zsh and [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)
        sudo aptitude install zsh
        sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
        chsh -s /bin/zsh
In gnome-terminal, select profile preference.
Make sure you're editing the 'default' profile, and go to the "Title and Command" tab.
Under "Command" there are three checkboxes: "Run command as a login shell", "Update login records when command is launched", and "Run a custom command instead of my shell".
I checked all three boxes, and under "Custom command:" I put zsh.
Close the terminal and restart the terminal."

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
add path in ~/.zshrc or /etc/profile.d/system_wide_path.sh and restart

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
        vi_cv_path_python=/home/ubuntu/Developer/ProgramFiles/python/Python-2.7.10/BuildFiles vi_cv_path_python3=/home/ubuntu/Developer/ProgramFiles/python/Python-3.4.3/BuildFiles ./configure --with-features=huge --enable-multibyte --enable-rubyinterp --enable-pythoninterp --enable-perlinterp --enable-luainterp --with-lua-prefix=/home/ubuntu/Developer/ProgramFiles/lua/lua-5.3.1/BuildFiles --enable-gui=gtk2 --enable-cscope --prefix=/home/ubuntu/Developer/ProgramFiles/vim/vim-7.4.843/BuildFiles
        make
        make install
        cd ../BuildFiles
        cd bin
        ln -s `pwd`/* ~/Developer/Path/bin/
        cd ../share
        ln -s `pwd`/* ~/Developer/Path/share/
        cd man
        ln -s `pwd`/* ~/Developer/Path/share/man
        cd man1
        ln -s `pwd`/* ~/Developer/Path/share/man/man1
        cd

###install zsh and [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)
        sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" 
        sudo aptitude install zsh
        chsh -s /bin/zsh
        echo "In gnome-terminal, select profile preference.\n\nMake sure you're editing the 'default' profile, and go to the "Title and Command" tab.\n\nUnder "Command" there are three checkboxes: "Run command as a login shell", "Update login records when command is launched", and "Run a custom command instead of my shell".\n\nI checked all three boxes, and under "Custom command:" I put zsh.\n\nClose the terminal and restart the terminal."

###[vim preference](https://github.com/peidong/vimrc)
        sudo aptitude install exuberant-ctags ack-grep git build-essential cmake python-dev
        cd ~
        git clone https://github.com/peidong/vimrc.git
        mv vimrc .vim
        ln -s ~/.vim/vimrc ~/.vimrc
        ln -s ~/.vim/ycm_extra_conf.py ~/.ycm_extra_conf.py
        git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim
Then vim, and :PluginInstall

        cd ~/.vim/bundle/YouCompleteMe
        ./install.py --clang-completer --omnisharp-completer --gocode-completer
        mkdir ~/.undo_history/