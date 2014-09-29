Ported to Windows LCOV Code Coverage tool
==================

[LCOV] (http://ltp.sourceforge.net/coverage/lcov.php) is a graphical front-end for GCC's coverage testing tool gcov. It collects gcov data for multiple source files and creates HTML pages containing the source code annotated with coverage information. It also adds overview pages for easy navigation within the file structure. LCOV supports statement, function and branch coverage measurement.

Installation
============

0. Install Perl if not installed. For example to **C:\Perl**
1. Open Windows Command Processor and run to create association (do not forget to change path to **perl.exe**)
    
    ```
    assoc .perl=Perl.File
    ftype Perl.File=C:\Perl\bin\perl.exe "%1" %* 
    ```

2. Define correct path of GCOV executable in **geninfo.perl**:
      
    ```
    our $gcov_tool = "C:\\CORRECT_PATH_TO\\gcov.exe";
    ```

3. Define correct path of Perl executable in **lcov.bat**:

    ```
    set perl=C:\CORRECT_PATH_TO\Perl.exe
    ```

HOW TO USE
==========

1. Compile your project to support [GCOV](https://gcc.gnu.org/onlinedocs/gcc/Invoking-Gcov.html#Invoking-Gcov). As a result *.gcno files will be created.
2. Run your binaries and *.gcda files will be created. You can place them to the same dir with *.gcno.
3. Go to a project root dir where *.gcda and *.gcno files placed.
4. Run **lcov.bat**

    
    ```
    d:\project> d:\lcov\lcov.bat
    Creating gcov\lcov.info ...
    Capturing coverage data from .
    d:\lcov/geninfo.perl . --output-filename gcov/lcov.info --base-directory .Found gcov version: 4.4.2
    Scanning . for .gcda files ...
    ```
    
5. After execution **gcov\html** dir will be created with html reports for current project.
