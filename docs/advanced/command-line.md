# Command Line Tool
The functionality of the user interface, for viewing the inputs to the wrangling process, viewing
the result, viewing how the result was produced, providing feedback, and steering the process,
has been described in the previous sections. Here we discuss how the user interface supports
the development of a wrangling activity over several sessions.
Importing a scenario. A scenario can be imported either from the command line or from
the web interface. There are two ways to import a scenario from the command line: either
importing a scenario file (option -i), or using a combination of the options -p -s -d -f, that describe
the wrangling properties, the source files, the data context, and feedback, respectively. More
details and examples of these options are provided in Section 7.1. Using the web interface, we
can import scenario files from the home page and the control panel page, with the same result
as using the -i command line option.
Exporting a scenario. A scenario can be exported from the command line using the -e option. Note that we could use the -e option to also export scenarios that were initialised in the
DataPreparer User Manual 49
October 13, 2020
command line with a combination of the options -p -s -d -f, that describe the wrangling properties, the source files, the data context, and feedback, respectively. More details and examples
of these options are provided in Section 7.1. Using the web interface, we can export scenario
files from the home page and the control panel page, with the same result as using the -e command line option.