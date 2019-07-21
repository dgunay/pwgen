#!/usr/bin/env perl

# Generates a password from random words.

use strict;
use warnings;

use List::Util qw( shuffle );
use Getopt::Long;

# Args
my $num_words = 4;
my $max_word_length = 0;
GetOptions(
  "words|n=i"       => \$num_words,
  "word-maxlen|l=i" => \$max_word_length,
) or die usage();

die "Must use 1 or more words\n" if $num_words < 1;

# Open the dictionary file
my $fh;
my @possible_words_locations = qw(/usr/share/dict/words /usr/dict/words);
for my $loc (@possible_words_locations) {
  open($fh, '<', $loc) or next;
  last if $fh;
}

die "Couldn't find a dictionary file on your system\n" unless $fh;

# Slurp the dictionary file into an array
my @words = ();
for my $word (<$fh>) {
  chomp $word;
  push @words, $word;
}

# Filter to words of a certain length if the user wants
@words = grep { length $_ <= $max_word_length } @words if $max_word_length > 0;

@words = shuffle @words;

die "Not enough words of length $max_word_length or less\n" if scalar @words < $num_words;

print "$_ " for @words[0..$num_words - 1];

## Subroutines

sub usage {
  return "Usage: pwgen [-n|--words=4] [-l|--word-maxlen=n]\n";
}
