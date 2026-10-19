SOs — Solomon's OS for the TI-84 Plus CE
SOs is an experimental launcher/interface project for the TI-84 Plus CE graphing calculator. The goal is to provide a simple menu for accessing calculator programs and files, with a reference section for common TI-84 features.
Project status: Development build. Features and build steps may vary with the calculator model, operating-system version, and CE C Toolchain version. Always test with copies of important files.

Features
- Programs menu: Lists supported program variables detected on the calculator and attempts to launch a selected program.
- Files browser: Displays information about detected calculator variables. Depending on the build, it may offer actions such as viewing details, archiving/unarchiving, or deleting a variable.
- TI-84 reference: A built-in guide to common calculator features, such as graphing, math, statistics, lists, matrices, and programming.
- GitHub Actions build: A workflow is provided to attempt an automated build and upload generated calculator files as a workflow artifact.
The reference guide is informational; it does not mean every built-in TI-84 function is reimplemented inside SOs.
Requirements
- A compatible TI-84 Plus CE calculator for on-device testing.
- The CE C Toolchain (CEdev) for compiling the source.
- A C project Makefile configured for CEdev.
- Git and GitHub, if you want to build through GitHub Actions.
Compatibility with other TI-84 models or operating systems is not guaranteed.
Repository layout
Your repository should contain the project's source files and build configuration. A typical layout may look like this:
.
├── .github/
│   └── workflows/
│       └── build.yml
├── src/
│   └── main.c
├── Makefile
└── README.md
Your actual repository may include additional source files, headers, libraries, or folders.
Build locally
1. Install a compatible version of CEdev using its official installation instructions.
2. Open a terminal in the directory containing the project's Makefile.
3. Run:
   make
4. Check the build output for the generated calculator file (commonly a .8xp program file, depending on the project configuration).
If make reports “No targets specified and no makefile found”, you are not in the directory containing the Makefile, or the Makefile is missing from the repository.
Build with GitHub Actions
1. Commit the source files and Makefile to your GitHub repository.
2. Ensure the workflow is saved as .github/workflows/build.yml.
3. Push to the main or master branch, open the repository's Actions tab, or run the workflow manually using Run workflow.
4. Open the completed workflow run.
5. Download the SOs-TI84CE-build artifact if the workflow successfully creates calculator files.
The workflow may need adjustments if the CEdev release archive, project layout, or Makefile differs from what it expects. A successful workflow run should not be assumed until the build log confirms compilation succeeded.
Install and test on the calculator
1. Build the project and locate the generated calculator file.
2. Transfer it using a compatible TI connectivity method, such as TI-Connect CE or another supported transfer utility.
3. Follow the transfer utility's instructions to send the file to the calculator.
4. Run SOs from the calculator's program menu.
5. Test the Programs and Files menus using nonessential test variables first.
Back up important calculator programs and data before testing. If a feature can archive, unarchive, or delete variables, verify its behavior with disposable test files before using it on anything important.
Troubleshooting
make: No targets specified and no makefile found
- Confirm that a Makefile is committed to the repository.
- Confirm that the workflow runs make from the directory containing that file.
- Check that the repository checkout includes the full project, not only the workflow file.
CEdev or cedev-config is not found
- Check the CEdev installation and the build log.
- Confirm the toolchain's bin directory is added to PATH.
- Check whether the workflow's download and extraction steps match the current CEdev release archive.
The build succeeds but no calculator file is uploaded
- Check the compiler output for the actual output filename and location.
- Confirm the output extension is included in the artifact collection step.
- Review the workflow logs for compilation errors or missing files.
A program does not launch or a file action fails
- Compatibility depends on the program type, calculator OS, and implementation.
- Test with a simple, nonessential program or variable.
- Save the complete error log and report the calculator model, OS version, and CEdev version when asking for help.
Contributing
Contributions, bug reports, and suggestions are welcome. When reporting a problem, include:
- The exact error message.
- The GitHub Actions step or local command that failed.
- The calculator model and OS version, when relevant.
- The CEdev version and any changes made to the project.
Disclaimer
SOs is an independent project and is not an official Texas Instruments product. Texas Instruments and TI-84 Plus CE are referenced for compatibility purposes. Use at your own risk and keep backups of important calculator d
