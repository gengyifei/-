# -
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。
/*
 * maxstr.c
 *
 *  Created on: 2019年10月24日
 *      Author: gyf
 */


#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int lengthOfLongestSubstring(char * s) {
    int table[0xFF];
    memset(table, -1, sizeof(table));
    int maxlen = 0;
    int idx = 0;
    int startidx = 0;
    int findidx = 0;
    int ch;
    while ((ch = s[idx]) != '\0') {

        findidx = table[ch];
        if (findidx >= startidx) {
            int len = idx - startidx;
            maxlen = len > maxlen ? len : maxlen;
            startidx = findidx + 1;
        }
        table[ch] = idx;
        ++idx;
    }
    int len = idx - startidx;
    maxlen = len > maxlen ? len : maxlen;
    return maxlen;
}

int main()
{
    printf("%d\n", lengthOfLongestSubstring("123a3cnbj3"));
}
