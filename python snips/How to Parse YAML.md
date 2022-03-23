# How to Parse YAML
https://stackoverflow.com/questions/8127686/parsing-a-yaml-file-in-python-and-accessing-the-data


## Questions
I am new to YAML and have been searching for ways to parse a YAML file and use/access the data from the parsed YAML.

I have come across explanations on how to parse the YAML file, for example, the PyYAML [tutorial](http://pyyaml.org/wiki/PyYAMLDocumentation#Tutorial), "[How can I parse a YAML file in Python](https://stackoverflow.com/questions/1773805/best-way-to-parse-a-yaml-file)", "[Convert Python dict to object?](https://stackoverflow.com/questions/1305532/convert-python-dict-to-object)", but what I haven't found is a simple example on how to access the data from the parsed YAML file.

Assume I have a YAML file such as:

```
 treeroot:
     branch1: branch1 text
     branch2: branch2 text
```

How do I access the text "branch1 text"?

"[YAML parsing and Python?](https://stackoverflow.com/questions/6866600/yaml-parsing-and-python)" provides a solution, but I had problems accessing the data from a more complex YAML file. And, I'm wondering if there is some standard way of accessing the data from a parsed YAML file, possibly something similar to "[tree iteration](http://lxml.de/tutorial.html#tree-iteration)" or "[elementpath](http://lxml.de/tutorial.html#elementpath)" notation or something which would be used when parsing an XML file?


## Top Answer
Since PyYAML's `yaml.load()` function parses YAML documents to native Python data structures, you can just access items by key or index. Using the example from the question you linked:

```
import yaml
with open('tree.yaml', 'r') as f:
    doc = yaml.load(f)
```

To access `branch1 text` you would use:

```
txt = doc["treeroot"]["branch1"]
print txt
"branch1 text"
```

because, in your YAML document, the value of the `branch1` key is under the `treeroot` key.

answered Nov 14, 2011 at 20:38

---

## Next Answer

Just an FYI on @Aphex's solution -

In case you run into -

> "*YAMLLoadWarning: calling yaml.load() without Loader=... is deprecated*"

you may want to use the `Loader=yaml.FullLoader` or `Loader=yaml.SafeLoader` option.

```
import yaml 

with open('cc_config.yml', 'r') as f:
    doc = yaml.load(f, Loader=yaml.FullLoader) # also, yaml.SafeLoader

txt = doc["treeroot"]["branch1"]
print (txt)
```

