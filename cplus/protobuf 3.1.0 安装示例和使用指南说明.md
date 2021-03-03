protobuf 3.1.0 ��װʾ����ʹ��ָ��˵��

˵��: �������Ӽ��� https://github.com/githublefantian/protobuf-3.1.0example.git
1��protobuf��google��˾��������ݴ洢��ʽ����ϸ���ܿ��Բο���https://code.google.com/p/protobuf/

2���������µ�protobufԴ���룬���ص�ַ��

https://github.com/google/protobuf/archive/v3.1.0.tar.gz

3������protobuf-3.1.0�汾��protobuf-3.1.0.tar.gz��ѹ�����а�װ��
��ѹ��tar xvzf protobuf-3.1.0.tar.gz
��װ���裺
��0��./autogen.sh
��1��./configure? --prefix=/usr/local/protobuf
��2��make
��3��make check
��4��make install

ע�⣺
?? ?��װ�ɹ��󣬽�����bin��libĿ¼�ֱ���뵽PATH��LD_LIBRARY_PATH�����������Է���ֱ�ӵ��á�

���û����������̣��༭/etc/profile�����ļ�ĩβ��ӣ�
export PATH=$PATH:/usr/local/protobuf/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/protobuf/lib
��ʱ�������һ�Ρ�

4���������ӣ�
?? ?1������һ��.proto�ļ����������ļ�Ϊ��lm.helloworld.proto

syntax = "proto3";

package lm;
message helloworld
{
??? required int32???? id = 1;? // ID
??? required string??? str = 2;? // str
??? optional int32???? opt = 3;? //optional field
}

�����Ŀ�����ԣ� protoc -I=./ --cpp_out=./?? lm.helloworld.proto

?? ?2����д c++�ļ���reader.cc? writer.cc


/*reader.cc*/���ļ���
#include "lm.helloworld.pb.h"
#include <iostream>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <string>
#include <pthread.h>
#include <fstream>

using namespace std;

void ListMsg(const lm::helloworld & msg) {
? cout << msg.id() << endl;
? cout << msg.str() << endl;
?}
?
int main(int argc, char* argv[]) {
? lm::helloworld msg1;
? {?? ?
??? fstream input("./log", ios::in | ios::binary);
??? if (!msg1.ParseFromIstream(&input)) {
????? cerr << "Failed to parse address book." << endl;
????? return -1;
??? }
? }
?
? ListMsg(msg1);?? ?
}




/*writer.cc*/ д�ļ���
#include "lm.helloworld.pb.h"
#include <iostream>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <string>
#include <pthread.h>
#include <fstream>
?
using namespace std;


int main(void)
?{
?
? lm::helloworld msg1;
? msg1.set_id(101);
? msg1.set_str("hello");
?? ?
? // Write the new address book back to disk.
? fstream output("./log", ios::out | ios::trunc | ios::binary);
?????? ?
? if (!msg1.SerializeToOstream(&output)) {
????? cerr << "Failed to write msg." << endl;
????? return -1;
? }??????? ?
? return 0;
?}



5���������C++���Ա���������Ӻ�׺���£�

ע�⣺���� ��Ҫָ��protobufͷ�ļ�λ�ú�protobuf�Ŀ��ļ�λ��? ���� -I/usr/local/protobuf/include ?-L/usr/local/protobuf/lib -lprotobuf -pthread

g++ reader.cc?? lm.helloworld.pb.cc?? -o reader? -I/usr/local/protobuf/include ?-L/usr/local/protobuf/lib -lprotobuf
g++ writer.cc?? lm.helloworld.pb.cc?? -o writer? -I/usr/local/protobuf/include ?-L/usr/local/protobuf/lib -lprotobuf


6�����н��

���� Writer �� Reader �Ľ�����£�
?>writer
?>reader
?101
?Hello


�������Ӽ��� https://github.com/githublefantian/protobuf-3.1.0example.git
��������������������������������
��Ȩ����������ΪCSDN������c�ַ��졹��ԭ�����£���ѭCC 4.0 BY-SA��ȨЭ�飬ת���븽��ԭ�ĳ������Ӽ���������
ԭ�����ӣ�https://blog.csdn.net/mircosheng/article/details/70141704