PostgreSQL在创建索引的时候会锁住锁住表，使得所有的写操作都被阻塞．注意这里仅仅是锁住写操作，读操作是不会被阻塞的．
假如创建索引的时间很长，那么所有的写操作将会被阻塞上数个小时，这再生产环境中显然是不可接受的．


#PostgreSQL
* Permission denied for relation

  Granting privileges on the database mostly is used to grant or revoke connect privileges. This allows you to specify who may do stuff in the database if they have sufficient other permissions.

  ANT on the database is not what you need. Grant on the tables directly.
  You want instead:

  PRIVILEGES ON TABLE side_adzone TO jerry;
  ANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO jerry;

* format output

  You have so many choices, how could you be confused :-)? The main controls are:

# \pset format
# \H
# \x
# \pset pager off
        Each has options and interactions with the others. The most automatic options are:

# \x off;\pset format wrapped
# \x auto
  The newer "\x auto" option switches to line-by-line display only "if needed".

  -[ RECORD 1  ]---------------
  id          | 6
  description | This is a gallery of oilve oil brands.
  authority   | I love olive oil, and wanted to create a place for
  reviews and comments on various types.
  -[ RECORD 2  ]---------------
  id          | 19
  description | XXX Test A
  authority   | Testing
  The older "\pset format wrapped" is similar in that it tries to fit the data neatly on screen, but falls back to unaligned if the headers won't fit. Here's an example of wrapped:
