### 二进制文件加解密

```
//二进制文件加解密
//读取二进制文件中的数据时，一个一个字符读取
//密码：password
void crpypt(char normal_path[], char crypt_path[],char password[]){
    //打开文件
    FILE *normal_fp = fopen(normal_path, "rb");
    FILE *crypt_fp = fopen(crypt_path, "wb");
    //一次读取一个字符
    int ch;
    int i = 0; //循环使用密码中的字母进行异或运算
    int pwd_len = strlen(password); //密码的长度
    while ((ch = fgetc(normal_fp)) != EOF){ //End of File
        //写入（异或运算）
        fputc(ch ^ password[i % pwd_len], crypt_fp);
        i++;
    }
    //关闭
    fclose(crypt_fp);
    fclose(normal_fp);
}
```

二进制文件记得加上小b，加密以后文件不能正常打开了，因为文件损坏了。

