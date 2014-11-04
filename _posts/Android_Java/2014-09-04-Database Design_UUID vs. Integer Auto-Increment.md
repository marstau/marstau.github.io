---
layout: post
title: Database Design/UUID vs Integer Auto-Increment
category: 游戏技术
tags: android／java
keywords: 
description: 
---

From :
<http://napkindrawing.blogspot.com/2009/01/database-design-uuid-vs-integer-auto.html>

We're doing some major database design at work and I raised the
possibility of using<span
class="Apple-converted-space"> </span>[UUID](http://en.wikipedia.org/wiki/Universally_Unique_Identifier)s
for all our<span class="Apple-converted-space"> </span>[surrogate
keys](http://en.wikipedia.org/wiki/Surrogate_key)<span
class="Apple-converted-space"> </span>as opposed to the traditional
per-table auto-incremented integer or sequence. I personally prefer
them, and we also have some special setup and needs that might benefit
from them. We have distinct databases per client, where some "partners"
span multiple clients (databases), I see this aiding in reporting across
databases. We also have a need for replication, possibly multi-master
replication as we're thinking about segregating bulk data-processing
(read+write) and daily usage (also read+write).

In the last few years, for my personal projects and some work projects,
I've switched to using official and ghetto mini-UUIDs wherever
auto-generated keys are used. For me, there wasn't a single revelation,
or one amazing article or book that changed my mind; it was more of a
gradual annoyance with simplistic database-generated keys.

My reasons have primarily been:

1.  **Less Database Dependency**<span
    class="Apple-converted-space"> </span>- When generated identifiers
    don't (have to) come from the database, business logic has less work
    to do when creating new data sets, especially when the new data is
    heavily interrelated, application code can simply declare a new key
    and reference it in other new, yet-to-be-saved objects. Also, having
    one authoritative source for generating keys - be it a lock on a
    table, or a global sequence provider - has a much lower threshold
    for scalability, and can invoke a sizeable performance penalty,
    especially in write-intensive applications. Modern UUID algorithms
    seem to be strong enough that a central "UUID Generation Service"
    per-host wouldn't be necessary.
2.  **Uniqueness**<span class="Apple-converted-space"> </span>- An
    object's or row's id will be unique across the table, database,
    server, and thankfully, most-likely, the entire universe. This truly
    means that for a given set of values, (hopefully guaranteed to be
    unique by database constraints), the id will never be used by
    another set of data. This makes error tracing, log analysis, and
    searching for old data trivial. Also, how many times have you typed
    up a query "DELETE FROM foo WHERE id=178", stared at it to make sure
    178 is the right number, hit enter, and then realized that "foo"
    should have been "bar"? Say goodbye to whatever had \#178 in "foo"!
3.  **Mocking/Testing**<span class="Apple-converted-space"> </span>-
    When id generation can happen in the application layer, creating
    large, complex data sets for testing/integration purposes is trivial
    and requires no back and forth to the database to associate objects.
    If you're using a full-featured ORM (e.g. Hibernate), this seems of
    no benefit, as you can create large sets of interrelated objects and
    tell the ORM to just save them all. But when these interrelated
    objects span databases, or application environments (all in a
    transactional environment, of course), it seems beneficial to let
    the application layer - the actual point where the new data set is
    created - specify the ID.
4.  **Data Privacy**<span class="Apple-converted-space"> </span>-
    Contemporary web applications often expose internal state through
    simplistic sequential integer IDs. How many times have you been at
    /foo.php?id=17443 and found interesting things when you go to
    /foo.php?id=17444 ? Though this should be mitigated by proper design
    and security, if UUIDs are used, the attack vector is nonexistent.

<span
style="display:inline! important;float:none;word-spacing:0px;font:13px/20px Verdana, sans-serif;text-transform:none;color:#333333;text-indent:0px;white-space:normal;letter-spacing:normal;background-color:#ffffff;text-align:left;widows:2;orphans:2;webkit-text-size-adjust:auto;webkit-text-stroke-width:0px;">I
initially started using a simplistic random 16-digit alphabetical string
to get the benefits described above, without having to deal with full-on
32 or 36 character UUIDs whilst programming and debugging. These are
currently in use on my web site, for example:</span>

> <http://napkindrawing.com/photo_view/rfenrcfouhnweeoo>

These are generated in application code by a function that weights
letter choices according to their frequency in the English language, so
you end up with almost pronounceable keys. In the database all surrogate
key columns have a default which produces hexadecimal digits if the
surrogate key is not specified. This has been helpful for debugging and
development, though given the weighting of the letters in English and
the<span class="Apple-converted-space"> </span>[Birthday
Paradox](http://en.wikipedia.org/wiki/Birthday_Paradox), I wouldn't feel
comfortable using this scheme on any large (billions of records)
databases. Plus it's completely non-standard and rather silly - you
could have a "random" key like "ohhhbuttbutthaha".

My last project at work used actual UUIDs as generated
by[Hibernate](http://hibernate.org/)'s<span
class="Apple-converted-space"> </span>[UUIDHexGenerator](http://www.hibernate.org/hib_docs/v3/api/org/hibernate/id/UUIDHexGenerator.html),
and the development overhead of - GOSH! - 32 character IDs was
nonexistant. Even dealing with handwritten queries whilst testing,
debugging and data analysis were much simpler when you don't have to
remember which "17" you're looking for in a fresh database.

The main complaints googling for "uuid database" seem to be around
adversely affected indexes where uuids are added in random numerical
order to clustered indexes - which would seem to be addressable by using
a timestamp-prefixed value, a simple "reverse(uuid())" in MySQL, for
example.

I'm of the opinion that the added hardware+software burden of supporting
32 byte keys is moderate to trivial given modern hardware, and the
benefits described above are enough of a reason to switch all instances
of generated keys to be UUIDs

 

 

However: in android:

Android does not impose any limitations beyond the standard SQLite concepts. We do recommend including an autoincrement value key field that can be used as a unique ID to quickly find a record. This is not required for private data, but if you implement a content provider, you must include a unique ID using the BaseColumns.\_ID constant.(from
: <http://developer.android.com/guide/topics/data/data-storage.html#db>)








