# �ϲ���֧��master

��������������dev��֧�ϣ���������������鿴��ǰ��֧
```
git branch
```
�տ�������Ŀ��ִ������������
```
git  add .
git  commit -m 'dev'
git push -u origin dev
```
Ȼ������Ҫ��dev��֧�Ĵ���ϲ���master��֧�� ����Σ�
�����л���master��֧��
```
git  checkout master
```
����Ƕ��˿����Ļ� ��Ҫ��Զ��master�ϵĴ���pull����
```
git pull origin master
```
������Լ�һ��������û�б�Ҫ�ˣ�Ϊ�˱����ڼ仹��pull
Ȼ�����ǰ�dev��֧�Ĵ���ϲ���master��
```
git  merge dev
```
Ȼ��鿴״̬
```
git status

On branch master
Your branch is ahead of 'origin/master' by 12 commits.
  (use "git push" to publish your local commits)
nothing to commit, working tree clean
```
�������˼��������12��commit����Ҫpush��Զ��master��
ִ�����������
```
git push origin master
```
�����Ϳ�����
