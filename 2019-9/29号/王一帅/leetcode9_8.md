给定两个单词（beginWord 和 endWord）和一个字典，找到从 beginWord 到 endWord 的最短转换序列的长度。转换需遵循如下规则：

每次转换只能改变一个字母。
转换过程中的中间单词必须是字典中的单词。
说明:

如果不存在这样的转换序列，返回 0。
所有单词具有相同的长度。
所有单词只由小写字母组成。
字典中不存在重复的单词。
你可以假设 beginWord 和 endWord 是非空的，且二者不相同。
示例 1:

输入:
beginWord = "hit",
endWord = "cog",
wordList = ["hot","dot","dog","lot","log","cog"]

输出: 5

解释: 一个最短转换序列是 "hit" -> "hot" -> "dot" -> "dog" -> "cog",
     返回它的长度 5。
示例 2:

输入:
beginWord = "hit"
endWord = "cog"
wordList = ["hot","dot","dog","lot","log"]

输出: 0

解释: endWord "cog" 不在字典中，所以无法进行转换。



~~~c
typedef struct my_trie {
	struct my_trie* arr[26];
	bool val;
} Trie;
Trie* trieCreate() {
	Trie* res = (Trie*)malloc(sizeof(Trie));
	for (int i = 0; i < 26; ++i)res->arr[i] = NULL;
	res->val = false;
	//res->val = '\0';
	return res;
}
void trieInsert(Trie* obj, char* word) {
	if (word != NULL)
	{
		if (word[0] != '\0')
		{
			if (obj->arr[word[0] - 'a'] != NULL)
			{
				trieInsert(obj->arr[word[0] - 'a'], word + 1);
			}
			else
			{
				Trie* temp = trieCreate();
				//temp->val = word[0];
				obj->arr[word[0] - 'a'] = temp;
				trieInsert(temp, word + 1);
			}
		}
		else
		{
			obj->val = true;
		}

```
}
```

}
bool trieSearch(Trie* obj, char* word,int size) {
	if (word != NULL)
	{
		for (int i=0;i<size;++i)
		{
			if (obj->arr[word[i] - 'a'] != NULL)
			{
				obj = obj->arr[word[i] - 'a'];
			}
			else
			{
				return false;
			}
		}
		return obj->val;
	}
	else
	{
		return true;
	}
}

void trieFree(Trie* obj) {
	for (int i = 0; i < 26; ++i)
	{
		if (obj->arr[i] != NULL)
		{
			free(obj->arr[i]);
		}
	}
	free(obj);
}
bool check(char* s1, char* s2, int size)
{
	int cnt = 0;
	for (int i = 0; i < size; ++i)
	{
		if (s1[i] != s2[i])
		{
			++cnt;
			if (cnt > 1)return false;
		}
	}
	return (cnt == 1);
}
int ladderLength(char* beginWord, char* endWord, char** wordList, int wordListSize)
{
	int size = strlen(beginWord);
	Trie* dict = trieCreate();
	for (int i = 0; i < wordListSize; ++i)
	{
		trieInsert(dict, wordList[i]);
	}
	int res = 0;
	if (trieSearch(dict, endWord, size))
	{
		Trie* done = trieCreate();
		int max = 8192;
		int start = 0, end = 0;
		char** queue = (char**)malloc(sizeof(char*) * max);
		queue[end++] = beginWord;
		for (int k=0;k<1000;++k)
		{
			int temp = end;
			for (int j = start; j %max!= end; ++j)
			{
				trieInsert(done, queue[j]);
				for (int i = 0; i < wordListSize; ++i)
				{
					if (check(queue[j % max], wordList[i], size))
					{
						if (strcmp(endWord, wordList[i]) == 0)
						{
							res = k + 2;
							break;
						}
						else if(!trieSearch(done,wordList[i],size))
						{
                            trieInsert(done,wordList[i]);
							queue[temp] = wordList[i];
							temp = (temp + 1) % max;
						}
					}
				}
				if (res > 0)break;
			}
			if (res > 0)break;
			start = end;
			end = temp;
			if (start == end)break;
		}
		trieFree(done);
        free(queue);
	}
	trieFree(dict);
	return res;
}
~~~

