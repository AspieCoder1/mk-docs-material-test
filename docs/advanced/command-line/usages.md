## Suggested Usages

The command line can be used in different ways. One approach is to use the configuration files for the initial information for a data preparation activity, and to do most of the real work from the visual interface. For the book promotions example, made available in the directory ManualBooks, this means running the command:

```bash
./datapreparer.sh
    -p ManualBooks/wrangle1.properties
    -s ManualBooks/sources.csv
    -d ManualBooks/datacontext.csv
```

Then most of the work is within the visual interface, from which sessions can be saved as described in the next section. Then the result can be viewed, the properties file tweaked, new sources added, etc, and the command run again. An alternative to the above would be running:

```bash
./datapreparer.sh
    -i ManualBooks/ManualBooks.scenario
```

However, it is also possible to use the command line extensively in development. This might involve running the following command line, exporting the result of the wrangling process into a csv file without accessing the web interface:

```bash
./datapreparer.sh
    -b
    -i ManualBooks.scenario
    -x ManualBooks/result.csv
```

Running the following command allows experimenting with a different set of wrangling properties (wrangle2.properties):

```bash
./datapreparer.sh
    -p ManualBooks/wrangle2.properties
    -s ManualBooks/sources.csv
    -d ManualBooks/datacontext.csv
```

Commands could be run in order to test different scenario outcomes, for instance running the following in Linux, would produce two end products, e1 and e2, as results of two different tests on a system property:

```bash
./datapreparer.sh
    -i s1.scenario
    -b
    -r 8181
    -o match.threshold=0.5 -x e1.csv
& ./datapreparer.sh
    -i s2.scenario
    -b
    -r 8182
    -o match.threshold=0.6 -x e2.csv
```

Another example, in Windows, would be running two scenarios with the same sources and data context but with different properties, to produce two end products:

```bash
datapreparer.bat
    -b
    -p ManualBooks/wrangle1.properties
    -s ManualBooks/sources.csv
    -d ManualBooks/datacontext.csv
    -r 8181
    -x result1.csv
datapreparer.bat
    -b
    -p ManualBooks/wrangle2.properties
    -s ManualBooks/sources.csv
    -d ManualBooks/datacontext.csv
    -r 8182
    -x result2.csv
```

You can combine the command line and user interface. The initial runs are performed using the command line and refined using the user interface. The command line is then used in production to apply the wrangling steps to the updated source files.
