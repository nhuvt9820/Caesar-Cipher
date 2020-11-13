#include <stdio.h>
#include <cs50.h>
#include <string.h>
#include <ctype.h>
#include <stdlib.h>

int main()
{
    printf("Chọn Kiểu Mã Hóa:\n");
    printf("Phép cộng nhập 1\n");
    printf("Phép nhân nhập 2\n");
    int CodeType = get_int("Kiểu mã: ");
    if((CodeType != 1) && (CodeType != 2))
            {
                printf("Phải nhập 1 hoặc 2");
                exit(0);
            }
    int Key = get_int("Key: ");
    if(CodeType == 2)
    {
        if(Điều kiện của key)
        {
            printf("Key must one of xxxx \n");
            exit(0);
        }
    }
    int HanhDong = get_int("Ma hoa nhap 1 \nGiai ma nhap 2\n: ");
    if((HanhDong != 1) && (HanhDong != 2))
            {
                printf("Phải nhập 1 hoặc 2");
                exit(0);
            }
    string text = get_string("Message: ");
    int error = 0 ;
    int L = strlen(text);
    char a[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    int n = 26;
    int m = strlen(text);
    char result[m];
    int K2;
    for (int i1 = 0; i1 < L; i1++)
    {
        if (text[i1] >= 48 && text[i1] <= 57)
        {
            printf("Text must only contain alphabetic characters.");
            exit(0);
        }
        else
        {
        }
    }
    //chọn ngôn ngữ
    if (CodeType == 1) //phép cộng
    {   //giải mã hay mã hóa
        if(HanhDong == 1) //mã hóa
        {
            for (int i = 0; i < m ; i++)
            {
                    if ((text[i] >= 'a' && text[i] <= 'z') || (text[i] >= 'A' && text[i] <= 'Z'))
                    {
                        if (text[i] >= 'A' && text[i] <= 'Z')
                        {
                            for (int j = 0; j < n; j++)
                            {
                                if (text[i] == a[j])
                                {
                                    result[i] = a[((j + Key) % 26)];
                                }
                            }
                        }
                        else if (text[i] >= 'a' && text[i] <= 'z')
                        {
                            for (int j = 0; j < n; j++)
                            {
                                if (text[i] == tolower(a[j]))
                                {
                                    result[i] = a[((j + Key) % 26)];
                                }
                            }
                        }
                    }
                    else
                    {
                        result[i] = text[i];
                    }
            }
        }
        else//giải mã
        {
            for (int i = 0; i < m ; i++)
            {
                if ((text[i] >= 'a' && text[i] <= 'z') || (text[i] >= 'A' && text[i] <= 'Z'))
                {
                    if (text[i] >= 'A' && text[i] <= 'Z')
                    {
                        for (int j = 0; j < n; j++)
                        {
                            if (text[i] == a[j])
                            {
                                if((j - Key) < 0)
                                {
                                    result[i] = a[(((j - Key) % 26) + 26)];
                                }
                                else
                                {
                                    result[i] = a[((j - Key) % 26)];
                                }
                            }
                        }
                    }
                    else if (text[i] >= 'a' && text[i] <= 'z')
                    {
                        for (int j = 0; j < n; j++)
                        {
                            if (text[i] == tolower(a[j]))
                            {
                                if((j - Key) < 0)
                                {
                                    result[i] = a[(((j - Key) % 26) + 26)];
                                }
                                else
                                {
                                    result[i] = a[((j - Key) % 26)];
                                }
                            }
                        }
                    }
                }
                else
                {
                    result[i] = text[i];
                }
            }
        }
    }
    //phép nhân
    else
    {
        if(HanhDong == 1) //mã hóa
        {
            for (int i = 0; i < m ; i++)
            {
                if ((text[i] >= 'a' && text[i] <= 'z') || (text[i] >= 'A' && text[i] <= 'Z'))
                {
                    if (text[i] >= 'A' && text[i] <= 'Z')
                    {
                        for (int j = 0; j < n; j++)
                        {
                            if (text[i] == a[j])
                            {
                                result[i] = a[((j * Key) % 26)];
                            }
                        }
                    }
                    else if (text[i] >= 'a' && text[i] <= 'z')
                    {
                        for (int j = 0; j < n; j++)
                        {
                            if (text[i] == tolower(a[j]))
                            {
                                result[i] = a[((j * Key) % 26)];
                            }
                        }
                    }
                }
                else
                {
                    result[i] = text[i];
                }
            }
        }
        else//giải mã
        {
            for (int i = 0;i < 27; i++)
            {
                if((Key * i) % 26 == 1)
                {
                    K2 = i;
                    break;
                }
            }
            for (int i = 0; i < m ; i++)
            {
                if ((text[i] >= 'a' && text[i] <= 'z') || (text[i] >= 'A' && text[i] <= 'Z'))
                {
                    if (text[i] >= 'A' && text[i] <= 'Z')
                    {
                        for (int j = 0; j < n; j++)
                        {
                            if (text[i] == a[j])
                            {
                                result[i] = a[((j * K2) % 26)];
                            }
                        }
                    }
                    else if (text[i] >= 'a' && text[i] <= 'z')
                    {
                        for (int j = 0; j < n; j++)
                        {
                            if (text[i] == tolower(a[j]))
                            {
                                result[i] = a[((j * K2) % 26)];
                            }
                        }
                    }
                }
                else
                {
                    result[i] = text[i];
                }
            }
        }
    }
    printf("result: ");
    for (int x = 0; x < m; x++)
    {
        printf("%c", result[x]);
    }
    printf("\n");
}
