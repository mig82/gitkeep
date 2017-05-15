# gitkeep

Sometimes when working with Git you require the folder structure of your project to be part of your repository. Maybe because you want to underline the importance of certain directories. Maybe some part of the logic depends on certain directories being there.

However, [Git is not currently capable of versioning directories](https://git.wiki.kernel.org/index.php/GitFaq#Can_I_add_empty_directories.3F). It only versions files. So if your directories are empty, they won't be versioned.

Gitkeep is an Ant build file that helps you create a `.gitkeep` file inside of every sub-directory of the base directory, in order to be able to force them to be versioned when pushing a project to Git.

The purpose of it is to simplify doing this:

    find . -type d -empty -exec touch {}/.gitkeep \;
    
AND to be able to get the same results even if you don't have the luxury of a Bash command line --i.e. If you work on Windows.

# Use

To create a `.gitkeep` in a specific directory called 'foo':

    ant -f gitkeep.xml gitkeep -Ddir foo

To create a `.gitkeep` file in every empty sub-directory:

    ant -f gitkeep.xml

To remove all `.gitkeep` files from every sub-directory:

    ant -f gitkeep.xml letgo

# Implementation Notes

Currently requires [Ant Contrib 0.6](http://ant-contrib.sourceforge.net/) to be downloaded and placed next to the build file.
