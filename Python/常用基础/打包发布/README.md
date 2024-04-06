# 打包发布

pipreqs ./ --encoding=utf-8

pip install virtualenv
virtualenv venv
cd venv
source ./bin/activate
deactive

python3 install -r requirements.txt

```
# 这是一个示例 Python 脚本。
from models import WordBasic


# 按 ⌃R 执行或将其替换为您的代码。
# 按 双击 ⇧ 在所有地方搜索类、文件、工具窗口、操作和设置。


def print_hi(name):
    # 在下面的代码行中使用断点来调试脚本。
    print(f'Hi, {name}')  # 按 ⌘F8 切换断点。


# 按间距中的绿色按钮以运行脚本。
if __name__ == '__main__':
    print_hi('PyCharm')

    words = WordBasic.select()
    for word in words:
        print(word.word, word.rank)

# 访问 https://www.jetbrains.com/help/pycharm/ 获取 PyCharm 帮助
```

requirements.txt

``` 
peewee==3.16.0
PyMySQL==1.1.0
```

```
from peewee import *


 database = MySQLDatabase('word_world',
                          **{'charset': 'utf8', 'sql_mode': 'PIPES_AS_CONCAT', 'use_unicode': True, 'host': 'localhost',
                             'user': 'root', 'password': '123456'})



class UnknownField(object):
    def __init__(self, *_, **__): pass


class BaseModel(Model):
    class Meta:
        database = database


class WordBasic(BaseModel):
    add_time = DateTimeField()
    add_user = BigIntegerField()
    american = CharField(null=True)
    chinese = CharField()
    deleted = IntegerField(constraints=[SQL("DEFAULT 0")])
    frequency = IntegerField(constraints=[SQL("DEFAULT 0")], null=True)
    help = CharField(null=True)
    human_word = CharField(null=True)
    id = BigAutoField()
    image = CharField(null=True)
    opposite = CharField(null=True)
    past = CharField(null=True)
    plural = CharField(null=True)
    pre = CharField(null=True)
    pronunciation = CharField(null=True)
    rank = IntegerField(constraints=[SQL("DEFAULT 0")], null=True)
    relative = CharField(null=True)
    remark = CharField(null=True)
    root = CharField(null=True)
    sentence = CharField(null=True)
    split = CharField(null=True)
    star = IntegerField(null=True)
    suffix = CharField(null=True)
    synonyms = CharField(null=True)
    tag = CharField(null=True)
    update_time = DateTimeField()
    update_user = BigIntegerField()
    video = CharField(null=True)
    web_chinese = CharField(null=True)
    word = CharField(unique=True)
    pronunciation_en = CharField(null=True)
    thirds = CharField(null=True)
    presenting = CharField(null=True)
    pasted = CharField(null=True)
    pasting = CharField(null=True)


    class Meta:
        table_name = 'word_basic'



```

