# mysql count distinct ͳ�ƽ��ȥ��

mysql��sql����У�count����ؼ�����ͳ�Ʊ��е�����,��

��һ��tableA�������������£�

id	name	age
1	tony	18
2	jacky	19
3	jojo	18


SELECT COUNT(age) FROM tableA
������������ܲ��table�����ж��������ݡ���ѯ�����3

��COUNT����ؼ����� DISTINCTһͬʹ��ʱ�����Խ�ͳ�Ƶ�������ĳ�ֶβ��ظ��������� �磺

SELECT COUNT(DISTINCT age) from tableA

�������Ĳ�ѯ����Ƕ�age���ֶε�ȥ�ء������2