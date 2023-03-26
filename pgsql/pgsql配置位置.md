> 除了已经提到的postgresql.conf 文件之外，PostgreSQL 使用另外两个需要手动编辑的配置文件，用于控制客户端认证，默认情况下，所有三个配置文件都存储在数据库集群的数据目录中

**pgsql有参数允许将配置文件放置在其他位置**
这样做可以<font color="#c300ff">简化管理</font>。尤其是当配置文件被单独存在时，更容易确保配置文件得到正确的备份

- `data_directory` (`string`)
 指定用于数据存储的目录。此参数只能在服务器启动时设置。

- `config_file` (`string`)
指定主服务器配置文件（通常称为postgresql.conf）。此参数只能在postgres命令行上设置。

- `hba_file` (`string`)
指定用于基于主机的身份验证（通常称为pg_hba.conf）的配置文件。此参数只能在服务器启动时设置。

- `ident_file` (`string`)
指定用于用户名映射（通常称为pg_ident.conf）的配置文件。此参数只能在服务器启动时设置。

- `external_pid_file` (`string`)
指定服务器应为服务器管理程序创建的附加进程标识（PID）文件的名称。此参数只能在服务器启动时设置。

希望配置文件存放在数据目录之外，则需要：
- 在`postgres -D`命令行执行
- 或PGDATA环境变量中指定包含配置文件的目录，并且必须在postgresql.conf（或命令行中）中设置data_directory参数，以指示数据目录的实际位置。
- 注意，data_directory会覆盖-D和PGDATA以确定数据目录的位置，但不能更改配置文件的位置

> 如果需要，您可以使用参数config_file，hba_file和/或ident_file单独指定配置文件名称和位置。 config_file只能在postgres命令行中指定，但其他选项可以在主配置文件`postgresql.conf`中设置。

### docker环境变量指定配置位置

### `PGDATA`
用于定义数据库文件的另一个位置，比如子目录。
默认为/var/lib/postgresql/data。
如果使用的数据卷是文件系统挂载点，或无法将其chowned到postgres用户的远程文件夹（例如某些NFS挂载），可以使用 initdb建议创建一个子目录以包含数据。

### `POSTGRES_INITDB_WALDIR`
设置WAL日志位置