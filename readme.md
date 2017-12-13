h2cppx(vim-port): parse the c++ header file and generate c++ implement code 
===========================================================================
**Purpose:** Parse the c++ header file and generate c++ implement code for vim plugin

**Required:** python 2.x

**Author:** xiaok

**External module required:** cheetah yaml(python package)

**Third-party(the plugin already include):** pyvisitor CppHeaderParser(modification) 

[Github-Link](https://github.com/xuqix/h2cppx.git)

Installation
------------
Before start, make sure you have installed the python package "yaml",
Then run below command:

    cd ~/.vim/plugin
    git clone 'https://github.com/xuqix/h2cppx.git

or you can use bundle to install it:

add `Plugin 'xuqix/h2cppx'` to ~/.vimrc and install it,then:

Now you can start using it.

After the installation is complete, 
You can map the key in .vimrc to quickly use the command.

    e.g:
    nmap <F3>  :H2cppx<ESC>
    nmap <F4>  :H2cppxLine<ESC>
    nmap <F3>p :CpH2cppx<ESC>
    nmap <F4>p :CpH2cppxLine<ESC>
    nmap <F5>  :H2cppxAuto<ESC>

Config
------
If the plugin can't find the python path in your computer,
you need set "g:python_path" in the .vimrc file like this:

    let g:h2cppx_python_path = '/usr/bin/python'

and you can specify the cppfile name extension like this:
(default value is 'cpp')

    let g:h2cppx_postfix = 'cxx'

five code-generate template file are provided by default,you 
can config it in '.vimrc' like this(template0-4,default is template1):

    let g:h2cppx_template = 'template4' 

if needed,you can refer to the default template and write your own template
files,and use absolute path config it :

    let g:h2cppx_template = '/home/xxx/.../xxx'

Finally,you can add a configuration file `.h2cppx_conf` in your project 
directory to help plugin search for cppfile,otherwise the plugin will find
cppfile in your header file directory.
The configuration file might look like:
    
    /home/test/temp/src
    src1
    src2

see the project_sample directory.

Usage
-----
The plugin function description:

* :H2cppx  
  Parse c++ header file and generate cpp file 

* :CpH2cppx  
  Like :H2cppx,but generat code in your clipboard, no file writed,you can use "p" to get it.

* :H2cppxLine  
  Generate cpp code in the cursor line,and append to the end of the cpp file

* :CpH2cppxLine  
  Like :H2cppxLine,but generat code in your clipboard, no file writed,you can use "p" to get it.

* :H2cppxAuto  (Recommendation)   
  Auto Contrast header and implementation files, find
  function declarations in the header file and append
  the newly added to the implementation file, if the 
  file does not exist to achieve a new file is created!

Example:
-------

    vim test.h
    :H2cppx  
    Now you can find new file "test.cpp" in your directory

    vim test.h
    :H2cppxLine
    Now you can find defined in your file "test.cpp" from current line of cursor 

    vim test.h
    :CpH2cppx  
    Like :H2cppx, but defined in your clipboard, no file writed, just use "p" to get it.

    vim test.h
    :CpH2cppxLine  
    Like :H2cppxLine, but defined in your clipboard, no file is writed.

    vim test.h
    :H2cppxAuto 
    Auto Contrast header and implementation files, find function 
    declarations in the header file and append the newly added to 
    the implementation file, if the file does not exist to achieve 
    a new file is created!

