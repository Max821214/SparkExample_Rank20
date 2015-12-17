## SparkExample Rank20  IMAC - BigData Team - 2015/12/16

###���D�y�z

�q[�ӫ~�������](http://files.imaclouds.com/dataset/HMC-Contest.log) ���A�C�X���P��̦n�ӫ~TOP20�C

###��ƫe�B�z

```
$ wget http://files.imaclouds.com/dataset/HMC-Contest.log
$ cat HMC-Contest.log | grep -o "act=order.*;e" | sed "s/;e//" > RankData
$ hadoop fs -put RankData /input/Rank
```
>�N��ư��e�B�z��A�i�H�N�����n����Ʊư��A�ѭ쥻��1.5G��ƭ��ܴXM�A���ɸ�ƳB�z�����R�į�

###������R

```
spark-submit --class com.imac.test.Main.class \
--master yarn-cluster Rank.jar \
/input/Rank/RankData \
/Spark/RankOutput
```
> �Ĥ@��```--class```�᭱��```Java```��```package name```�M```class name```
> �ĤG��--master ���ϥ��O���Ҧ��A�o��ĥ�yarn-cluster�A�᭱��```Jar```
> �ĤT��M�ĥ|����O����J��ƩM��X�ؿ�

###��X���G
>���R���\��A�i�H�ϥ�```hadoop fs -cat /Spark/RankOutput/part-00000```���O�C�X���G�A�p�U:

```
01 0006584093
02 0000143511
03 0007082051
04 0005772981
05 0014252066
06 0006323656
07 0004607050
08 0024239865
09 0003425855
10 0004134266
11 0006993652
12 0004862454
13 0009727250002
14 0006270095
15 0014252055
16 0006993663
17 0009727290016
18 0018504861
19 0000143500
20 0024634260
```