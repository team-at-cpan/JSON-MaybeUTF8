# NAME

JSON::MaybeUTF8 - provide explicit text/UTF-8 JSON functions

# SYNOPSIS

    use JSON::MaybeUTF8 qw(:v1);
    binmode STDOUT, ':encoding(UTF-8)';
    binmode STDERR, ':raw';
    (*STDOUT)->print(encode_json_text({ text => '...' }));
    (*STDERR)->print(encode_json_utf8({ text => '...' }));

# DESCRIPTION

Combines [JSON::MaybeXS](https://metacpan.org/pod/JSON%3A%3AMaybeXS) with [Unicode::UTF8](https://metacpan.org/pod/Unicode%3A%3AUTF8) to provide
4 functions that handle the combinations of JSON and UTF-8
encoding/decoding.

The idea is to make the UTF-8-or-not behaviour more explicit
in code that deals with multiple transport layers such as
database, cache and I/O.

This is a trivial wrapper around two other modules.

## BOM removal

The `$JSON::Maybe::UTF8::REMOVE_BOM` flag is **set by default** due
to [https://github.com/rurban/Cpanel-JSON-XS/issues/125](https://github.com/rurban/Cpanel-JSON-XS/issues/125). If you would
prefer to disable this, add `$JSON::Maybe::UTF8::REMOVE_BOM = 0;`
in your code.

Note that this only affects things when [Cpanel::JSON::XS](https://metacpan.org/pod/Cpanel%3A%3AJSON%3A%3AXS) is used (preferred by [JSON::MaybeXS](https://metacpan.org/pod/JSON%3A%3AMaybeXS)
if it can be loaded).

## decode\_json\_utf8

Given a UTF-8-encoded JSON byte string, returns a Perl data
structure. May optionally remove the UTF-8 [BOM](https://en.wikipedia.org/wiki/Byte_order_mark#UTF-8)
if it exists.

## encode\_json\_utf8

Given a Perl data structure, returns a UTF-8-encoded JSON
byte string.

## decode\_json\_text

Given a JSON string composed of Unicode characters (in
Perl's internal encoding), returns a Perl data structure.

## encode\_json\_text

Given a Perl data structure, returns a JSON string composed
of Unicode characters (in Perl's internal encoding).

## encode\_json\_text

Given a Perl data structure, returns a formatted JSON string composed
of Unicode characters (in Perl's internal encoding).

This is functionally identical to ["encode\_json\_text"](#encode_json_text), but with
indentation to make it readable, and with defined key ordering which
should make it easier to `diff` two different data structures.

# AUTHOR

Tom Molesworth <TEAM@cpan.org>

# LICENSE

Copyright Tom Molesworth 2017-2021. Licensed under the same terms as Perl itself.
