H:\���ͱ���

### һ��׼������

1. ��װgit��
2. ע��github���½�һ������Ĳֿ�(username.github.io)��
3. ��װnode.js��



### ������װhexo������ʼ��

�ο������̳̣�

<https://hexo.io/zh-cn/index.html>

```linux
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```



![1563978429421](C:\Users\yansheng\AppData\Roaming\Typora\typora-user-images\1563978429421.png)



### ������������

1. Ĭ��������`landscape`,�����Ǻܺÿ���һ�㶼��������⡣

2. ���ڱȽ����е������漸�֣�

     2.1. next: <https://github.com/iissnan/hexo-theme-next>����ֹͣ���£����ߣ��µģ�

   <https://github.com/theme-next/hexo-theme-next>

   ![1563986574404](C:\Users\yansheng\AppData\Roaming\Typora\typora-user-images\1563986574404.png)

     2.2. yilia: <https://github.com/litten/hexo-theme-yilia>

![1563986365828](C:\Users\yansheng\AppData\Roaming\Typora\typora-user-images\1563986365828.png)



3. ��ѡ����yilia:

   #### ��װ

   ```
   $ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
   ```

   #### ����

   �޸�hexo��Ŀ¼�µ� `_config.yml` �� `theme: yilia`

   <font color="red">ע�⣺���������ʽ������ʱ��ð�ź���Ҫ��Ӣ�Ŀո�����ļ������������ע�ͣ�ͳһ���ļ���ʽΪUTF-8</font>��

   #### ����

   ```
   cd themes/yilia
   git pull
   ```

   ����

   ```
   hexo clean
   hexo generate
   hexo server
   ```

   ��������ʣ�<http://localhost:4000/>��ע������ڼ䲻�ܰ�ֹͣ����`Ctrl+C`,��Ȼ��ֹͣ����ҳ��404��

   

   Ч��ͼ��

   ![1563987355476](C:\Users\yansheng\AppData\Roaming\Typora\typora-user-images\1563987355476.png)



### �ġ���hexo����github����

#### 1. �޸�hexo��Ŀ¼�µ� `_config.yml`

```
# ����github�Ĳֿ�
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: https://github.com/yansheng836/yansheng836.github.io.git
  branch: master
```



#### 2.�޸ĸ�Ŀ¼�µ�`.gitignore`

.gitignore��ԭ���ݣ�

```gitignore
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

�������ӣ�

```
#ignored the useless themes
/themes/landscape/
```



#### 3.����github������`hexo deploy`

����������ƴ���

```
ERROR Deployer not found: git
```

���git֧�֣�

```
npm install hexo-deployer-git --save
```



Ϊ��Ŀ���˵��README.md���޸�hexo��Ŀ¼�µ� `_config.yml`��

```
#hexo g ��Ĭ�Ͻ�����md�ļ�ת���ɣ���Ⱦ�ɣ�HTML�ļ��ŵ�public�ļ����У�������仰����˼����
#����hexo�Ľ�������������Ⱦ(skip_render)README.md�ļ�
skip_render: 
 - 'README.md'
```



