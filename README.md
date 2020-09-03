## Separatrice

Separatrice is able to split a text into sentences and a sentence into clauses (russian). This approach uses regular exression and
some information about grammatical parameters of the words in a sentence. Such approach can be useful for parsing texts in social media 
that are often written in informal style with some typos or even mistakes. Note, that for formal and well-written langauge there are 
good neural-network-based splitters, such as ![razdel][https://github.com/natasha/razdel] 

## Get Started

```
from separatrice import Separatrice

sep = Separatrice()

sep.into_clauses('Ненавижу кабачки, их кто-то изобрел специально для того, чтобы люди их сажали, не зная, зачем.')

['Ненавижу кабачки',
 'их кто-то изобрел специально для того',
 'люди их сажали, не зная, зачем.']
```

## Evaluation

It needs to say that a nortion of clause is debatable. In my project I assume that a clause is a part of the sentence that contains a verb, explicitly or
implicitly. For example, "Это мой друг, он бегает по утрам.". The first clause 'Это мой друг' contains an implicite verb 'быть', whereas the second one
is with an explicite verb 'бегать'.

So, as validation data I use sentences from social media and Q&A dialogs.

Main problem is the omitting comma with сonjunction 'и'. Like

```
'Есть 1млн коротких строк англ языка(допустим из библии), юзер начинает вводить строку и надо подобрать наиболее подходящую по смыслу.'
                                                                                     -----
```

For now, I do not see way to improve it without harming other results.
