[![Build Status](https://travis-ci.org/mcmillhj/File-Dedup.svg?branch=master)](https://travis-ci.org/mcmillhj/File-Dedup)
[![Coverage Status](https://coveralls.io/repos/mcmillhj/File-Dedup/badge.png?branch=master)](https://coveralls.io/r/mcmillhj/File-Dedup?branch=master)
[![Kwalitee status](http://cpants.cpanauthors.org/dist/File-Dedup.png)](http://cpants.charsbar.org/dist/overview/File-Dedup)

# NAME

File::Dedup - Deduplicate files across directories

# VERSION

version 0.007

# SYNOPSIS

    use File::Dedup;
    File::Dedup->new( directory => '/home/hunter/', recursive => 1 )->dedup;

    or 

    use File::Dedup
    my $deduper = File::Dedup->new( 
       directory => '/home/hunter/', 
       recursive => 1, 
       ask       => 0,
       simulate  => 1,
       debug     => 0,
    );
    $deduper->dedup;

# DESCRIPTION

A small utility to identify duplicate files in a given directory and optionally delete them

# NAME 

File::Dedup

# ATTRIBUTES 

- `directory`

    Directory to start searching for duplicates in. \[required\]

- `ask`

    Ask which file have to be removed or keep first file if not defined.

- `debug`

    Optionally dump file name and checksum to stdout.

- `simulate`

    Optionally simulate, which files will be removed.
    Output could be used for manual removal (grep and remove `simulate: `). Ex.:
    ```
    simulate: rm -rf '<file name>'
    ```

- `recursive`

    Recursively search the directory tree for duplicates. \[optional\]

- `group`

    \*NOT YET IMPLEMENTED\*. Instead of deleting duplicates this option will write all duplicates into their own subfolders for deletion at the user's leisure.

# METHODS

- `dedup`

    Identifies and eliminates duplicate files based on the options supplied by the user. 

# AUTHOR

Hunter McMillen <mcmillhj@gmail.com>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2015 by Hunter McMillen.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
