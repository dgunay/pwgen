# pwgen

Generates passphrases from your Linux installation's dictionary file.

## Requirements

Perl with `List::Util` and `Getopt::Long`.

For now, Linux only (it is hardcoded to use either `/usr/share/dict/words` or 
`/usr/dict/words`.

## Usage

```
$ pwgen [-n|--words=4] [-l|--word-maxlen=n]\n
```

It will generate a 4 word passphrase by default. You can adjust the maximum length of 
the words used with `-l` or `--word-maxlen`.

## Future work

I wrote this in like 20 minutes so it could of course use some improvements (PRs welcome).

Some tests would be cool I guess. Mainly to verify it does what the usage text says it does.

The linux system dictionary has some really, really weird words that are difficult to 
memorize. A setting to use a custom dictionary file, or to filter out dumb words no one 
uses like "Transjordanian" would really help. For now, filtering to words of 4 or 5 letters
in length kind of helps.
