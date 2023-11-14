# seagull
personal blog in markdown; more than archive

## Content

日记 -> daily


在Linux系统中，可以使用以下步骤来重置SQL数据库的密码：

1. 打开终端，并使用root用户或具有sudo权限的用户登录到Linux系统。
2. 执行以下命令以停止SQL服务：
   ```
   sudo systemctl stop mysql
   ```
3. 执行以下命令以以跳过权限验证的方式启动SQL服务：
   ```
   sudo mysqld_safe --skip-grant-tables &
   ```
4. 打开另一个终端窗口，并使用以下命令连接到SQL服务器：
   ```
   mysql -u root
   ```
5. 在MySQL命令行界面中，选择要重置密码的数据库：
   ```
   use mysql;
   ```
6. 执行以下命令来更新用户的密码：
   ```
   update user set authentication_string=password('新密码') where User='用户名';
   ```
   请将"新密码"替换为您想要设置的新密码，将"用户名"替换为要重置密码的用户名。
7. 执行以下命令以刷新权限表：
   ```
   flush privileges;
   ```
8. 执行以下命令以退出MySQL命令行界面：
   ```
   exit;
   ```
9. 返回到第一个终端窗口，并执行以下命令以停止跳过权限验证的SQL服务：
   ```
   sudo pkill mysqld
   ```
10. 最后，执行以下命令以重新启动SQL服务：
    ```
    sudo systemctl start mysql
    ```

请注意，上述步骤中的命令可能因您使用的Linux发行版和SQL服务器版本而有所不同。确保根据您的实际情况进行相应的调整。

