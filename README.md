# test
/*
*for test github
*/

include<stdio.h>
int main()
{
        int  pid0,pid1;
        int x = 1;
        pid0 = fork();
        pid1 = fork();
        if( pid0 == 0 ) {
                printf(" child0: x = %d\n ", ++x);
                printf("child0: pid0 = %d\n ",pid0);
//              exit(0);
        }
        if( pid1 == 0 ) {
                printf(" child1: x = %d\n ", ++x);
                printf("child1: pid1 = %d\n ",pid1);
//              exit(0);
        }
        printf("parent: x = %d\n ",--x);
        printf("parent: pid0 = %d\n ",pid0);
        printf("parent: pid1 = %d\n ",pid1);
        exit(0);
}



此时执行的是pid0 = fork（）；代码起点就是从pid0= fork（）开始

child0: x = 2
child0: pid0 = 0
 child1: x = 3 ，执行子进程pid1 下的代码，共享了 pid0 下x =2等变量 ,所以是x=3
 child1: pid1 = 0
 parent: x = 2
 parent: pid0 = 0
 parent: pid1 = 0
 child0: x = 2
 child0: pid0 = 0
 parent: x = 1
 parent: pid0 = 0
 parent: pid1 = 3254

此时执行的是pid1 = fork（）；代码起点就是从pid1 = fork（），开始时x =1 开始
 child1: x = 2
 child1: pid1 = 0
 parent: x = 1
 parent: pid0 = 3253
 parent: pid1 = 0

最后执行的是父进程main；
 parent x = 0
 parent: pid0 = 3253
 parent: pid1 = 3255
