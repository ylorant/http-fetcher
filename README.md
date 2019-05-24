# http-fetcher

Short tool to fetch files from remote sources, and split them according to a config. Usually used with Hedgebot's HoraroTextFile. It can help you create source text files to use as OBS text sources, to enable janky p.

# How to use

To use it, you have to create a JSON configuration file. A sample configuration is provided in the file `sample-config.json`. 
The config file contains 3 basic parameters and a complex one:

- `input`: This parameter refers to the path of the file to get. You can use the standard PHP streams enabled on your system with this parameter.
- `time`: The refresh time for the input file, in seconds.
- `split`: The string to split the input file text in multiple parts to be reinjected into the output files.
- `output`: This is the complex setting, to configure each output file. It is an array of objects, each one defining an output file. The parameters of this object are as follows:
    - `file`: The file path to output to.
    - `content`: The content template. Use the `$X` marker to put text from the input file into the output file, according to its index in the split input text.

Once you made your config file, you can just start the script like this :

```
php http-fetcher.php -c my-config.json
```