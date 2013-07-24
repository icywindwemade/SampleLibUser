This project shows how to use a Xcode static library, as Part 2 of the two projects.
The first project is SampleLibrary.  <git@github.com:icywindwemade/SampleLibrary.git>

The following steps illustrates how it is done:

    1. First create the library repo on Github.
        => Note the 'git remote add origin <url>' command.
    2. Library Project creation
       a. Create the Xcode project, iOS Static Library,
       b. remove .m file; do not include Foundation in header and Frameworks.  
       c. In Build Phases -> Add header files.
       d. Build for Debug/Simulator
       e. Although the product .a file is still red, the actual file get created without problem.
       f. Commit the changes from Xcode version control
    3. Repository connection, the following commands are used:
      git remote add origin <url>
      find . -name "*xcuserstate" > .gitignore 
      commit again, now the Xcode should always found xcuserstate file as uncommited file.
      git rm --cached `cat .gitignore `
      git commit -m "Remove unwanted file"
      git push -u origin master
      ==> Now Xcode should be able to commit and push changes to Github
    4. Close Xcode project 
    5. git submodule add <Library Repo>
    6. drag and drop the library project file into the user project.
    7. TestNetwork->Build Phase->Target Dependencies->Add <library>.a
    8. TestNetwork->Build Phase->Link Binary with Libraries->Add <library>.a
    9. Coding: #include "<submodule project name>/<header file>"


