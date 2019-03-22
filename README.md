# NAME

JSON::MaybeUTF8 - provide explicit text/UTF-8 JSON functions

# SYNOPSIS

    use JSON::MaybeUTF8 qw(:v1);
    binmode STDOUT, ':encoding(UTF-8)';
    binmode STDERR, ':raw';
    (*STDOUT)->print(encode_json_text({ text => '...' }));
    (*STDERR)->print(encode_json_utf8({ text => '...' }));

# DESCRIPTION

Combines [JSON::MaybeXS](https://metacpan.org/pod/JSON::MaybeXS) with [Unicode::UTF8](https://metacpan.org/pod/Unicode::UTF8) to provide
4 functions that handle the combinations of JSON and UTF-8
encoding/decoding.

The idea is to make the UTF-8-or-not behaviour more explicit
in code that deals with multiple transport layers such as
database, cache and I/O.

This is a trivial wrapper around two other modules.

## decode\_json\_utf8

Given a UTF-8-encoded JSON byte string, returns a Perl data
structure.

## encode\_json\_utf8

Given a Perl data structure, returns a UTF-8-encoded JSON
byte string.

## decode\_json\_text

Given a JSON string composed of Unicode characters (in
Perl's internal encoding), returns a Perl data structure.

## encode\_json\_text

Given a Perl data structure, returns a JSON string composed
of Unicode characters (in Perl's internal encoding).

# AUTHOR

Tom Molesworth <TEAM@cpan.org>

# LICENSE

Copyright Tom Molesworth 2017. Licensed under the same terms as Perl itself.
