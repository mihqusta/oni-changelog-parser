# ONI Changelog Parser

This tool aims to assist in creating update logs for the Oxygen Not Included Wiki.

It is not fully automatic. The posts on the official update channel are not semantically sound, so mistakes are unavoidable. Read through the output! There are quick configuration constants at the top of the script, you might find you want to tinker with the code. Please share your progress!

The program outputs text files in the `./out/` directory.

##### Usage:

python3 main.py [-h] [--feed FEED] [-n ENTRIES] prefix

##### Examples:

> $ python main.py U39

fetch the latest update, use the prefix 'U39' for update name

> $ python main.py -n 10 U40

fetch the latest 10 updates

> $ python main.py --feed Some_Expansion EX2

fetch the latest update for some future expansion development feed



## `phrasemap.json`

This file contains rules for suggestions for the `affectedPages` attribute.

Before matching, the text is converted to lowercase, so keys should only contain lowercase letters. Characters `()"'?!.,;:` are removed, keys cannot contain these either.

In the example string `Liquid Oxygen Mask` with rules `"liquid oxygen": ["Liquid Oxygen"]` and `"oxygen mask": ["Oxygen Mask"]` only the first rule is matched, as matches cannot overlap.

If one key is a subset of another, the longer one takes precedence. Rule `"sounds for experiment 52b": []` and (more importantly) rule `"experiment 52b sounds": []` both have priority over rule `"experiment 52b": ["Experiment 52B"]`.