En:DoubleDetection
==================

Date: 2014-06-26 00:01:35

added Double Document Detection

**Neue Seite**

<div>

=Double Document Detection=\
The most simple way to detect double content is the comparison of the
URL. That is the only double content detection which is made during
document crawling, but this is not sufficient for good search results.
YaCy uses several heuristics to detect double content. The result of the
evaluation of these heuristics is the setting of double-detection flags
which can then be used in \[\[En:Ranking\|ranking rules\]\] to shift
such doubles to the end of the search result list or to remove them
completely. The following methods are available:\
\
==Detect URLs with/without \'\'www.\'\'-prefix in Host Names==\
This is a very simple rule with simply compares the host names and
detects that the same url appears again with or without a \'\'www\'\'
subdomain. The result of that detection is written to the flag\
www\_unique\_b\
During crawltime the flag \'\'www\_unique\_b\'\' is assigned true if and
only if the host name has a subdomain \'\'www\'\'. If the crawl does
urls without a \'\'www\'\' in the host name then the flag would always
be false even if the url is unique. This is incorrect and corrected
during postprocessing: for every url in the postprocessing, it is
checked if for each url with \'\'www\_unique\_b\'\'=false actually no
url with \'prefix\' is present. If so, then the flag is turned into
true. The result of that process is, that you can use
\'\'www\_unique\_b\'\' in boost querys and filter queries in the
\[\[En:Ranking\|ranking rules\]\] to remove or boost double urls to the
end of the result list.\
The preference to prefer urls with the subdomain \'\'www\'\' can be
switched to the opposite using the flag
\'\'search.ranking.uniqueheuristic.preferwwwprefix\'\' in the yacy.conf
settings.\
\
==Detect URLs with/without http(s) Service==\
This is also a very simple rule and very much the same as the detection
of \'\'www\'\' subdomains but now for http and https protocols. The
result of that detection is written to the flag\
http\_unique\_b\
During crawl time the flag is assigned true if and only if the protocol
is \'\'https\'. If the crawl is finished, then for every url with
protocol \'\'http\'\' it is checked if the same url is present with
protocol \'https\'\'. If no such url is present, the flag
\'\'http\_unique\_b\'\' is assigned true as well. The flag can be used
the same way as \'\'www\_unique\_b\'\' in the \[\[En:Ranking\|ranking
rules\]\].\
The preference to prefer urls with the protocol \'\'https\'\' can be
switched to the opposite using the flag
\'\'search.ranking.uniqueheuristic.preferhttps\'\' in the yacy.conf
settings.\
\
==Detect Double Documents Based on Exact Content Signatures==\
The detection of double content is based on a hash of the textual
content of the document. Each time a document is parsed, the text part
is hashed and the hash is written to an index field. Each time a new
document is created, the computed text hash is also searched within the
complete set of all known document. In case that a document is therefore
unknown by the exact hash, the field\
exact\_signature\_unique\_b\
is assigned true; for every another document which has the exact hash
identical to any other document, the field
\'\'exact\_signature\_unique\_b\'\' is assigned false. After the crawl
is finished, a postprocessing counts the number of documents with the
same extact hash and writes the number of such copies into the field\
exact\_signature\_copycount\_i\
The flag \'\'exact\_signature\_unique\_b\'\' can be used in the
\[\[En:Ranking\|ranking rules\]\] for filter or boost queries, the
number \'\'exact\_signature\_copycount\_i\'\' can be used for boost
functions.\
\
==Detect Double Documents Based on Fuzzy Content Signatures==\
Double content is not so easy to discover if two document have almost
the same content, but differ only in a small number of details. To
discover such double content, a document hash is computed based on a
document profile which is computed using a statistical analysis of the
number of occurrences of words in the document. If a document is unique
based on the fuzzy signature profile, then the flag\
fuzzy\_signature\_unique\_b\
is set to true. The exact process to compute the signature calculates an
MD5 hash of a plain text \"profile\" of a page. The algorithm to
calculate a page \"profile\" takes the plain text version of a page and
performs the following steps:\
\* remove all characters except letters and digits, and bring all
characters to lower case,\
\* split the text into tokens (all consecutive non-whitespace
characters),\
\* discard tokens equal or shorter than MIN\_TOKEN\_LEN (default 2
characters),\
\* sort the list of tokens by decreasing frequency,\
\* round down the counts of tokens to the nearest multiple of QUANT =
QUANT\_RATE \* maxFreq, where QUANT\_RATE is 0.01f by default, and
maxFreq is the maximum token frequency. If \<code\>maxFreq\</code\> is
higher than 1, then QUANT is always higher than 2 (which means that
tokens with frequency 1 are always discarded).\
\* tokens, which frequency after quantization falls below QUANT, are
discarded.\
\* create a list of tokens and their quantized frequency, separated by
spaces, in the order of decreasing frequency.\
The setting for \'\'MIN\_TOKEN\_LEN\'\' and \'\'QUANT\_RATE\'\' can be
done in the servlet at /ContentAnalysis\_p.html. These values influence,
how \'fuzzy\' the attribute works.\
After the crawl is finished, a postprocessing counts the number of
documents with the same extact hash and writes the number of such copies
into the field\
fuzzy\_signature\_copycount\_i\
The flag \'\'fuzzy\_signature\_unique\_b\'\' can be used in the
\[\[En:Ranking\|ranking rules\]\] for filter or boost queries, the
number \'\'fuzzy\_signature\_copycount\_i\'\' can be used for boost
functions.\
\
==Detect Double Documents Based on Title Comparison==\
In cases that all document titles are unique in a crawl (and only in
such cases) the detection of double content is possible using the flag\
title\_unique\_b\
This flag works the same as the flag \'\'exact\_signature\_unique\_b\'\'
with the only difference, that the whole title is compared instead of
the hash of the full text.

</div>