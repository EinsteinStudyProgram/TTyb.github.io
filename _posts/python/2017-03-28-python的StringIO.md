---
layout: post
categories: [python]
title: python��StringIO
date: 2017-03-22
author: TTyb
desc: "python��StringIO"
---

��ʱ����Ҫ�� `information` �����ڱ��أ���������д��

```
file = open("filename","w")
file.close()
file.close()
```

������ʱ����д�����أ�ֻ��Ҫ���ڵ����ڴ�ͺã������Ϳ����� `StringIO` ���б��棺

```

import StringIO
s = StringIO.StringIO()
s.write(messages)
s.seek(0)
getmessages = s.read()
s.close()
```

`StringIO` �����а��ж�ȡ `readlines` ������д�� `writelines` ,һ������ļ�д��ķ��������У������뿴��

>https://docs.python.org/2/library/stringio.html