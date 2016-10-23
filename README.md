# 记录自己的学习

坚持学习，提升自己。

## Program Language
* [Java编程思想《Thinking in Java》](http://java.vagrants.win)

## Web
 * [豆瓣开发工程师《Python Web开发实战》](http://flask.vagrants.win)

## 机器学习

{%ace edit=true, lang='python', theme='monokai'%}
import numpy as np


def apk(actual, predicted, k=10):
    if len(predicted)>k:
        predicted = predicted[:k]
    score = 0.0
    num_hits = 0.0
    for i,p in enumerate(predicted):
        if p in actual and p not in predicted[:i]:
            num_hits += 1.0
            score += num_hits / (i+1.0)
    if not actual:
        return 0.0
    return score / min(len(actual), k)

def mapk(actual, predicted, k=10):
    return np.mean([apk(a,p,k) for a,p in zip(actual, predicted)])


if __name__ == '__main__':
    actual = (['4','2','1','31a'],['1','2'])
    predict = (['1','3','5','4'],['1','2'])
    print(apk(actual,predict,k=4))
    print(mapk(actual,predict,k=4))
{%endace%}