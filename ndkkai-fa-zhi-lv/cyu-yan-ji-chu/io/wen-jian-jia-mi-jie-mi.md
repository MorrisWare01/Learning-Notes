### 文件加密、解密

用简单的异或运算进行加密，解密的话就是一个逆过程。

规则：1^1=0, 0^0=0, 1^0=1, 0^1=1 同为0，不同为1

```
void crpypt(char* filePath, char* crpyptFilePath){

    //打开文件，返回文件的指针
    FILE* f_read = fopen(filePath, "r");
    FILE* f_write = fopen(crpyptFilePath, "w");

    //文件是否成功打开
    if (f_read == NULL || f_write == NULL){
        printf("文件打开失败");
        return;
    }

    int ch;//一次读取一个字符，每一个字符都是一个数据，用int来表示
    //EOF End Of File = -1
    while ((ch = fgetc(f_read)) != EOF){
        fputc(ch ^ 9, f_write);//用异或运算进行加密
    }

    //关闭文件
    fclose(f_read);
    fclose(f_write);
}

void main(){

    //文件路径
    char* path = "D:\\test.txt";
    char* path_new = "D:\\test_new.txt";

    //文件加密crpypt
    crpypt(path, path_new);

    //文件解密decrpypt，是一个逆过程，注意先把原来的文件删除
    crpypt(path_new, path);

    system("pause");
}
```



