# mysql
## mysql 触发器

前提 <br>
有两个表 t_student(id,studentName,studentDesc) t_user(id,userName)

t_user 用来收集 insert 操作的t_student 数据
例如 在 t_student 表中添加了一个字段（null,'张三','3年2班'）的话，会自动的在t_user 上生成 一行数据（null,'张三'）；这就是触发器。 <br>

``` sql查询
create TRIGGER insert_student_to_user 
AFTER INSERT ON t_student FOR EACH ROW
BEGIN
INSERT INTO t_user VALUES(null,NEW.studentName);
END
```


