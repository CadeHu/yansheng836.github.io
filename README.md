# **���ͱ���**

### һ��׼������

1. ��װgit��
2. ע��github���½�һ������Ĳֿ�(username.github.io)��
3. ��װNode.js��



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



![eZEIaj.jpg](https://s2.ax1x.com/2019/07/25/eZEIaj.jpg)











### ������������

1. Ĭ��������`landscape`,�����Ǻܺÿ���һ�㶼��������⡣

2. ���ڱȽ����е������漸�֣�

     2.1. next: <https://github.com/iissnan/hexo-theme-next>����ֹͣ���£����ߣ��µģ�

   <https://github.com/theme-next/hexo-theme-next>

   ![eZE5ZQ.jpg](https://s2.ax1x.com/2019/07/25/eZE5ZQ.jpg)

     2.2. yilia: <https://github.com/litten/hexo-theme-yilia>

![eZEhqg.jpg](https://s2.ax1x.com/2019/07/25/eZEhqg.jpg)



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

   ![eZEoIs.jpg](https://s2.ax1x.com/2019/07/25/eZEoIs.jpg)
   
   



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



��hexo��Ŀ¼���½��ֿ⣬���ڹ���д����֧��֮ǰ�Ĳ���github��Ϊ�����֧��

```
git init
git remote add origin https://github.com/yansheng836/yansheng836.github.io.git

```

Ϊ���㽫yilia���������ý���ͬ������ʵ�������Ѿ��ܾ�û�����ˡ�������ֱ��ɾ��/themes/yilia/�µ�.gitɾ����



����һ����֧���д�����ݣ�����ͬ����ͬһ�ֿ�Ĳ�ͬ��֧�����ύһ�Σ���Ȼ�ᱨ`fatal: Not a valid object name: 'master'.`

```
git add .
git commit -m "init the blog"
```

������֧����ͬ����github��blog��֧

```
git branch blog
git checkout blog
git push origin blog
```



### �塢������github pages

����master��֧Ϊ��ҳ�����ͨ��`<https://yansheng836.github.io/>`����



����й��������������ö�Ӧ����������ֱ����/source/���`CNAME`�ļ�(ע�⣺���ļ�û�к�׺)������Ϊ������

```
www.yansheng.xyz
```

�ɹ�����setting�л���ʾ��ͨ���������ʣ�������ԭ����·����



### ��������򵥸��Ի�����

�������еĸ�����ϢΪ�Լ��ġ�

�ο���[����򵥸��Ի�����](./blog/docs/����򵥸��Ի�����.md)

