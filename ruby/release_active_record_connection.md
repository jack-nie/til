call clear_active_connections!.

We run ActiveRecord in an environment where we make use of JMS on a TorqueBox server, and we had to do something similar in order to ensure connections were freed.

As a caveat, you will also need to do this if you spawn a Thread which makes use of ActiveRecord, since (in ActiveRecord 3.2 certainly) the thread id is used as part of the connection checkout process.

A pattern we use repeatedly is the following:

    def with_connection(&block)
      ActiveRecord::Base.connection_pool.with_connection do
        yield block
      end
    ensure
      ActiveRecord::Base.clear_active_connections!
      ActiveRecord::Base.connection.close
    end
    which you could use like this:

    with_connection do
      do_things_with_activerecord_db_and_get_some_parameters()
    end
