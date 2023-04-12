# 13504: Robotic Palletizer and Conveyance


## Objective and Repo Scope:


## Branch Structure:

Due to the large amount of systems in the project, and the amount of integrated systems, this repo has a set of branch-mediated releases, with each branch having cetain commit requirements. They are as follows:

 * dev: 		the working branch. Commits do not have to result in self-consistent code. It is meant to document progress from the programmer
 * dev-release:		a development release. Not for commits, only branch merges from dev. Each new node in this branch is a set of code that fully works for all systems (PLC, HMI, ROBOT, etc.)
 * dev-$FEATURE:	similar to the dev working branch, but meant to work on a specific feature.
 * dev-$DEVELOPER-$FEATURE	similar to the dev working branch, but done by a dev menat for a specific feature.
 * release:		The branch for releases, which are all the code releases meant to operate in "production" for a reasonable amount of time. They also include releases meant to test system capabilities (like FAT and SAT releases)
 * hotfix:		development branch for hotfies and issues that arise during production. Finished fixes are merged into release


## Folder structure:

 * ./samples/						: generic code samples. each subfolder in this folder is for a specific sample
 * ./samples/$SAMPLE_NAME/job/				: job files, .JBI
 * ./samples/$SAMPLE_NAME/conf/				: controller configuration files (.PRM, .DAT, etc)
 * ./samples/$SAMPLE_NAME/controller/			: Controller CMOS.BIN backups, zip files of full controller backups and full controller backups as files, including teach pendant files and MotoPlus apps

 * ./modules/						: Placeholder for modules or discrete augmentations to the YRC platform (such as Palletsolver, conveyor tracking, etc).
 * ./modules/$MODULE_NAME
 * ./modules/$MODULE_NAME/doc
 * ./modules/$MODULE_NAME/src

 * ./motoplus/						: Sample MotoPlus modules and implementation
 * ./motoplus/src					: Source for MotoPlus modules and ancillary code
 * ./motoplus/module					: Module executable and other executable codes
 * ./motoplus/doc					: Documentation 
 * ./doc/						: General YRC dcumentation


## Commit vs branch notes:

### Robot and Sysmac files:

Generally, if a change is made to 



### YRC files

Due to the large number of dependencies between the job files, configuration files, MotoPlus modules, etc. it is hard to understand at a glance if a given commit has all the correct files to run the system. Also, it is hard to gauge if the system performs correctly without loading everything from the controller.

To fix this, each commit should occur only once it is validated in motosim or in the robot controller. Each commit should also include **all the files that changed** since the last commit, whether they are configuration files or job files.

The best way to ensure this is to run a full controller backup or to back up all the files, and copy/paste into the correct folder. Git will automatically identify what has changed and what hasn't.

Generally, a commit should result in working code, more than any other normal software repo. 	