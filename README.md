# mysql
## mysql 触发器

前提 <br>
有两个表 t_student(id,studentName,studentDesc) t_user(id,userName)

t_user 用来收集 insert 操作的t_student 数据
例如 在 t_student 表中添加了一个字段（null,'张三','3年2班'）的话，会自动的在t_user 上生成 一行数据（null,'张三'）；这就是触发器。 <br>

``` sql
create TRIGGER insert_student_to_user 
AFTER INSERT ON t_student FOR EACH ROW
BEGIN
INSERT INTO t_user VALUES(null,NEW.studentName);
END
```
``` sql
create trigger 触发器名称
触发条件(before | after )(insert | update| delete) ON 哪一个表  FOR EACH ROW (FOR EACH ROW为固定格式)
BEGIN 
 操作
END
```

查看结果：<br>
![图片1](https://github.com/Zhangchao999/mysql/raw/master/picture/trigger/1.png)
![图片2](https://github.com/Zhangchao999/mysql/raw/master/picture/trigger/2.png)

