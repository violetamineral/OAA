# OAA(Oracle Advanced Analytics)

오라클 DB에서 제공하는 Data Mining 툴에 대해 알아보도록 하겠습니다.
기본적으로 Data Mining을 사용하기 위해서는 DB의 AA Option을 enable하여야 합니다.
또한, Mining은 SQL, R, Data Miner을 사용하여 분석할 수 있습니다.

## DB서버에 접속하여 다음과 같이 AA 옵션을 활성화하십시오.

<pre><code>
 > cd $ORACLE_HOME/bin
 > srvctl stop database -d Sales(DB고유이름)
 > chopt enable oaa
 > srvctl start database -d Sales
</code></pre>

## 다음은 마이닝용 사용자를 만들어주세요.
<pre><code>CREATE USER dmuser IDENTIFIED BY Oracle123456
       DEFAULT TABLESPACE USERS
       TEMPORARY TABLESPACE TEMP
       QUOTA UNLIMITED ON USERS;
Commit;
</code></pre>

## 마이닝을 위한 권한을 부여합니다.
<pre><code>GRANT CREATE MINING MODEL TO dmuser;
GRANT CREATE SEQUENCE TO dmuser;
GRANT CREATE TABLE TO dmuser;
GRANT CREATE PROCEDURE TO dmuser;
GRANT CREATE SYNONYM TO dmuser;
GRANT CREATE VIEW TO dmuser;
GRANT CREATE SESSION TO dmuser;
GRANT CREATE TYPE TO dmuser;
GRANT CREATE JOB TO dmuser;
GRANT CREATE ANY DIRECTORY TO dmuser; 
GRANT SELECT ANY MINING MODEL TO dmuser;


GRANT EXECUTE ON CTXSYS.CTX_DDL TO dmuser;
REVOKE SELECT ANY MINING MODEL FROM dmuser;
</code></pre>

## SQLDeveloper에서 Data Miner를 활용하실 경우, Data Miner Repository를 설치해 주십시오.
https://www.oracle.com/webfolder/technetwork/tutorials/obe/db/12c/r1/dm/dm_41/ODM12c-41_SetUp.html


**혹시 SQLDeveloper로 접속해서 DataMiner Repository Install Message가 뜨지 않는 경우는 
SQL_Developer_Home\sqldeveloper\dataminer\scripts 해당 경로의 스크립트 실행


https://docs.oracle.com/cd/E55747_01/doc.41/e58244/GUID-B6792DA2-CECB-4692-9927-2C6D11CCE8D5.htm#DMRIG160
