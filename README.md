# A Ubuntu'esque name generator

*There are only two hard things in Computer Science: cache invalidation and naming things.*

*[Phil Karlton](https://skeptics.stackexchange.com/questions/19836/has-phil-karlton-ever-said-there-are-only-two-hard-things-in-computer-science)*

Unique ids are required constantly for naming hosts, services, infrastructure, etc.  In the same spirit as Ubuntu with ts random and catchy '<adjective> <animal>' release cycle, provided here is a Bash program that can assist in generating similar identifiers.

By default it will generate '<adjective>-<animal>-<numbers>', but it has options for pulling from scientists, plants, etc. as well as the ability to limit phrase length and the seperator.

The credit for the source word dictionaries goes to [bschiffhaler](https://github.com/bschiffthaler/mkname), who create a C language program that would generate an Ubuntu-like identifier.

## Invoking

```
git clone https://github.com/fabianlee/mkname.git
cd mkname

# generate unique id
./mkname.sh
```

## Options

```
$ ./mkname.sh -h
./mkname.sh [-h] -L <seperator_char> -m <max_chars_per_section> -M <max_chars_total> [-d <adjectives,animals,numbers>]

-h	help
-L	seperator character between words, default '_'
-m	max characters per section, default=10
-m	max characters per section, default=40
-d	CSV list of sections, default=adjectives,animals,numbers,characters

EXAMPLES:

Example of building '<adjective>-<plant>'
./mkname.sh -d adjectives,plants

Example of building '<adjective>-<number>-<scientist>' with max 8 chars per phrase
./mkname.sh -d adjectives,numbers,scientists_last -m8

Example of building '<scientist>_<number>' max 20 chars per phrase, 40 chars total
./mkname.sh -L '_' -d scientists_last,numbers -m20 -M40

Example of building '<animal> <letters> <numbers>' allow uppercase
./mkname.sh -L ' ' -d animals,letters,numbers -m20 -M40 -c0
```

## Dictionaries

* `animals` - [List of animals by common name](https://en.wikipedia.org/wiki/List_of_animals_by_common_name)
* `plants` - [List of plants by common name](https://en.wikipedia.org/wiki/List_of_plants_by_common_name)
* `scientists_full` - [Full names of famous scientists](https://www.famousscientists.org/list/)
* `scientists_last` - [Last names of famous scientists](https://www.famousscientists.org/list/)
* `lovecraft` - Nouns in H.P. Lovecraft's combined works with a frequency (>10) and some extra. Manually curated

