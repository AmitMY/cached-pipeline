# Pipeline
This class manages your runtime components in terms of order and caching.

## Intuition
Usually, you have a few components, each calculating something and passing some outputs to be used in the next components.
Further, when you change a single component, you have to re-run everything, which can take some time.

We construct the pipeline in a way that every function running can use any other output, and can supply its output to all other components.

To solve the re-running problem, every output from a step in the pipeline is cached, and if a file exists, it only needs to read the file and not re-run the function.

## Example
The repository [Chimera](https://github.com/AmitMY/chimera) for example, uses the pipeline to pre-process, model, and post-process deep-learning problems which take hours to run.
Without any manual caching, saving of models, etc, they can now load any step of their model under a second.

Output example of the pipeline first run:
![First Run Pipeline](https://github.com/AmitMY/chimera/blob/master/git-assets/first-run.png?raw=true)
