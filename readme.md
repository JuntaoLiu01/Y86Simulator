## Y86 Pipeline 
#####д֮ǰӦ���ָ���Ƿ񱻶�  
#####ÿ��ʱ�����ڣ�ÿ����ˮ�ߴӻ�������ȡ��ִ��ָ�� �������д����һ����ˮ�ߵĻ�����

## Fetch  
�Ƚ���pcUpdate  
��ָ��洢����ȡ������ֵ������д��D��
- server �˿�49936  
- client ����Decode_server  

����  
- PC
- PrePC

## Decode  
���8���Ĵ���
��ȡ�Ĵ���������ð�գ�����д��E��  
- ����Memory
- ����writeback

## Execute  
ALU���㣬����д��M��  
- server �˿�49940
- client ����Memory_server  
����  
ifun,rA,rB,valC,valP

## Memory  
���memory
��д�ڴ棬д��WriteBack��
- server �˿�49942
- client ����WriteBack_server  
����  
ifun,valC,valA,valB,desE,desM,srcA,srcB

## Writeback  
д�ؼĴ���
- server �˿�49944
- client ����

### ʱ���߳�
## ���е�tcp����
client|server|cid
------|------|---
Fetch|WriteBack|1
Fetch|Memory|2
Fetch|Decode|3
Decode|Execute|4
Decode|Memory|5
Decode|Writeback|6
Execute|Memory|7
Memory|Writeback|0


## ��������
�㲥��ַ��37877
�����ʼ���Ӻ�
ÿ��client����ָ�����϶˿ڹ㲥  
��ʽ
```json
{
    "id":1,
    "level":"F",
    "ip":"192.168.1.1",
    "port":43396
}
```
��ָ���Ķ˿ڼ�����Ҫ�Ĺ㲥�����������ӣ��ٴι㲥�Լ�����������
```json
{
    "id":2,
    "cid":3
}
```
ʱ���̼߳�������PCUpdate��һ��,��������������Ƿ���ɣ�����Ժ��͹㲥��ʼ
```json
{
    "id":3   
}
```
��ʼ֮�����ÿ���׶ε��Ƿ���ɣ������ɹ㲥��һ�����ڽ���
```json
{
    "id":4,
    "step":23
}
```
�ȴ��ض�ʱ����ٴη���ʱ���źţ����������׶�״����
����ʱ��Write_back�㲥����
```json
{
    "id":5
}
```


## y86�㲥��ʽ
ȡ������
```json
{
    "id":0
}
```
�㲥�Լ���level,������Ӱ�ť��ÿ���ͻ���ÿһ�뷢��һ�θ�����
```json
{
    "id":1,
    "FLevel":True,
    "DLevel":True,
    "ELevel":True,
    "MLevel":True,
    "WLevel":False
}
```
��master�㲥�Լ��ѽ�������
```json
{
    "id":2,
    "cid":6
}
```
master�㲥��ʼ
```json
{
    "id":3
}
```