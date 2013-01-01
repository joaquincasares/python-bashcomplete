`python-bashcomplete` takes:

* Lists of strings and dictionaries, or
* Nested dictionaries

and compiles simple, yet functional bashcomplete code for any program that
invokes bashcomplete.BashComplete() with a list or dictionary.

# Example structures

Autocompletes one level:

    test = ['level1a', 'level1b']

Autocompletes two possibilities, both of which have sublevels:

    test = {
        'level1a': ['1', '2', '3'],
        'level1b': ['4', '5', '6']
    }

Autocompletes three possibilities, only two of which have sublevels:

    test = [
        {
            'level1a': ['1', '2', '3']
        },
        {
            'level1b': ['4', '5', '6']
        },
        'level1c'
    ]

Autocompletes only one level. Final string values are ignored:

    test = {
        'level1a':{'a'},
        'level1b':{'b'}
    }

# Generation

Add the following lines to your command-line program:

    import bashcomplete
    bashcomplete.BashComplete(test)

where `test` is your data structure. This will generate
`<filename>.bash_complete` in your current folder using the filename of the
executing program.

If you wish to constrain the autocomplete words to what has been defined,
use:

    bashcomplete.BashComplete(test, constrain=True)

# Usage

Use the generated `<filename>.bash_complete` by adding:

    . /path/to/<filename>.bash_complete

to your `.profile`. From this point on, any run of `<filename>` will use the
generated bash completion.
