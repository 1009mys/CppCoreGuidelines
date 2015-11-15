<a name="S-naming"></a>
# NL: �̸������ �ڵ� ��ġ ��Ģ
> # NL: Naming and layout rules

���� �ٸ� ������ ���ٸ� �ϰ��� �̸������ ��ġ�� ������ �ȴ�. �̴� "�� ��Ÿ���� ����� �ͺ��� �� ����"��� ���Ǹ� �ּ�ȭ�� �� �ֱ� �����̴�.
�׷��� �������� �ſ� �پ��� ��Ÿ�ϵ��� �־� ������� �װ͵鿡 ���� (��������) �����ϴ�.
�Դٰ� ��κ��� ���� ������Ʈ���� ���� ����(sources)���κ��� �ڵ带 �����Ͽ�, ��� �ڵ带 ���� ��Ÿ�Ϸ� ǥ��ȭ�ϴ� ���� ���� �Ұ����ϴ�.
���⼭ �� ���� ���̵� ���ٸ� ����� �Ϸ��� ��Ģ�� �Ұ��ϸ�, ��¥ ��ǥ�� Ư�� ��Ģ ������ �ƴ� �ϰ����̴�.
IDE��� ������ ������ �� �ִ�. (�Դٰ� ���ص� �� ���̴�.)
> Consistent naming and layout are helpful. If for no other reason because it minimizes "my style is better than your style" arguments.
However, there are many, many, different styles around and people are passionate about them (pro and con).
Also, most real-world projects includes code from many sources, so standardizing on a single style for all code is often impossible.
We present a set of rules that you might use if you have no better ideas, but the real aim is consistency, rather than any particular rule set.
IDEs and tools can help (as well as hinder).

�̸������ ��ġ ��Ģ:
> Naming and layout rules:

* [NL 1: Don't say in comments what can be clearly stated in code](#Rl-comments)
* [NL.2: State intent in comments](#Rl-comments-intent)
* [NL.3: Keep comments crisp](#Rl-comments-crisp)
* [NL.4: Maintain a consistent indentation style](#Rl-indent)
* [NL.5: Don't encode type information in names](#Rl-name-type)
* [NL.7: Make the length of a name roughly proportional to the length of its scope](#Rl-name-length)
* [NL.8: Use a consistent naming style](#Rl-name)
* [NL 9: Use `ALL_CAPS` for macro names only](#Rl-all-caps)
* [NL.10: Avoid CamelCase](#Rl-camel)
* [NL.15: Use spaces sparingly](#Rl-space)
* [NL.16: Use a conventional class member declaration order](#Rl-order)
* [NL.17: Use K&R-derived layout](#Rl-knr)
* [NL.18: Use C++-style declarator layout](#Rl-ptr)
* [NL.25: Don't use `void` as an argument type](#Rl-void)

��κ��� ��Ģ���� �������̰� �����ڵ��� ���� �ǰ��� �����Ѵ�.
IDE ���� �⺻�� �ܿ� �پ��� ����� ������ �ִ� �����̴�. �� ��Ģ���� ������ ���� �ʴ´ٸ� �⺻���� �������� ���ȵȴ�.
> Most of these rules are aesthetic and programmers hold strong opinions.
IDEs also tend to have defaults and a range of alternatives. These rules are suggested defaults to follow unless you have reasons not to.

�� ��ü���̰� �������� ��Ģ���� �����ϱ� ���� ���̴�.
> More specific and detailed rules are easier to enforce.

<a name="Rl-comments"></a>
### NL.1: �ڵ忡�� ��Ȯ�ϰ� ��Ÿ�� �� �ִ� ������ �ּ����� ���� ����
> ### NL.1: Don't say in comments what can be clearly stated in code

**�ٰ�**
> **Reason**

�����Ϸ��� �ּ����� ���� �ʴ´�.
�ּ����� �ڵ庸�� �� ��Ȯ�ϴ�.
�ּ����� �ڵ�� ���� �ϰ��ǰ� ������Ʈ���� �ʴ´�.

> Compilers do not read comments.
Comments are less precise than code.
Comments are not updated as consistently as code.

**�߸��� ��**
> **Example, bad**

    auto x = m*v1 + vv;	// m�� v1�� ���ϰ� ����� vv�� ���� // multiply m with v1 and add the result to vv

**�����ϱ�**
> **Enforcement**

����ü ������ �����ϴ� �ΰ����� ���α׷��� ����� C++�� �� ǥ���� �� �ִ��� ���캸��.
> Build an AI program that interprets colloquial English text and see if what is said could be better expressed in C++.

<a name="Rl-comments-intent"></a>
### NL.2: �ּ����� �ǵ��� ��Ÿ����
> ### NL.2: State intent in comments

**�ٰ�**
> **Reason**

�ڵ�� ������ ������ �ƴ϶� ������ �ߴ����� ���Ѵ�. ���� �ּ��� ������ ���뺸�� �� ��Ȯ�ϰ� �����ϰ� �ǵ��� ��Ÿ�� �� �ִ�.
> Code says what is done, not what is supposed to be done. Often intent can be stated more clearly and concisely than the implementation.

**����**
> **Example**

    void stable_sort(Sortable& c)
        // sort c in the order determined by <, keep equal elements (as defined by ==) in their original relative order
    {
        // ... quite a few lines of non-trivial code ...
    }

**���� ����**
> **Note**

�ּ��� �ڵ尡 ���� �ʴٸ�, �� �� �߸��� ���ɼ��� �ִ�.
> If the comment and the code disagrees, both are likely to be wrong.

<a name="Rl-comments-crisp"></a>
### NL.3: �ּ��� �����ϰ� ��������
> ### NL.3: Keep comments crisp


##### �ٰ�
> ##### Reason

��Ȳ���� ���ظ� ������ �ϰ� �װ�(�ּ�)�� �ҽ� ���� �ȿ� �����־� �ڵ带 �� �б� ��ư� �����.
> Verbosity slows down understanding and makes the code harder to read by spreading it around in the source file.

##### Enforcement

�Ұ����ϴ�.
> not possible.

<a name="Rl-indent"></a>
### NL.4: �ϰ����� �鿩���� ��Ÿ���� ��������
> ### NL.4: Maintain a consistent indentation style

**�ٰ�**
> **Reason**

������(���). "����� �Ǽ���"�� ����.
> Readability. Avoidance of "silly mistakes."

**�߸��� ��**
> **Example, bad**

    int i;
    for (i = 0; i < max; ++i); // ���� �߻��� ��ٸ��ϴ�! // bug waiting to happen
    if (i == j)
        return i;

**�����ϱ�**
> **Enforcement**

������ �������.
> Use a tool.

<a name="Rl-name-type"></a>
### NL.5 �̸� �ȿ� Ÿ�� ������ �������� ����
> ### NL.5 Don't encode type information in names

**�̷��� �ٰ�**: �̸��� ��ɼ����ٴ� Ÿ���� �ݿ��Ѵٸ�, �̴� ��ɼ��� �����ϱ� ���� ���� Ÿ���� �ٲٱ� ��ư� �� ���̴�.
Ÿ���� ������ �̸��� ��Ȳ�ϰų� �Ƹ����� �� �ִ�.
�밡���� ǥ����� �־��̴�. (��� ���� ���� Ÿ�� �� �־�)

> **Rationale**: If names reflects type rather than functionality, it becomes hard to change the types used to provide that functionality.
Names with types encoded are either verbose or cryptic.
Hungarian notation is evil (at least in a strongly statically-typed language).

**Example**

    ???

**���� ����**
> **Note**

� ��Ÿ���� ���������� �ɹ������� �����ϰų�, ���������� �����Ϸ��� �Ѵ�.
> Some styles distinguishes members from local variable, and/or from global variable.

    struct S {
        int m_;
        S(int m) :m_{abs(m)} { }
    };

�̰��� �������� �ʴ�.
> This is not evil.

**���� ����**
> **Note**

� ��Ÿ���� Ÿ�԰� Ÿ���� �ƴ� ���� �����Ϸ��� �Ѵ�.
> Some styles distinguishes types from non-types.

    typename<typename T>
    class Hash_tbl {	// maps string to T
        // ...
    };

    Hash_tbl<int> index;

�̰��� �������� �ʴ�.
> This is not evil.

<a name="Rl-name-length"></a>
### NL.7: �̸��� ���̸� �װ��� ������ ���̿� �뷫 ����ϰ� ������
> NL.7: Make the length of a name roughly proportional to the length of its scope

**�̷��� �ٰ�**: ???
> **Rationale**: ???

**��**
> **Example**

    ???

**�����ϱ�**
> **Enforcement**

???

<a name="Rl-name"></a>
### NL.8: �ϰ����� �̸����� ��Ÿ���� �������
> ###  NL.8: Use a consistent naming style

**�̷��� �ٰ�**: �ϰ����� �̸������ �̸����� ��Ÿ���� �������� �����ش�.
> **Rationale**: Consistence in naming and naming style increases readability.

**���� ����**
**Note**

���� ��Ÿ���� �����ϰ� ���� ���� ���̺귯���� ����� ��, ���� �ٸ� ��Ģ�� ��� ���� ���� ����.
"house style"�� �����ϵ�, "������" ���̺귯���� ������ ��Ÿ���� ���ܵд�.
> Where are many styles and when you use multiple libraries, you can't follow all their differences conventions.
Choose a "house style", but leave "imported" libraries with their original style.

**��**
> **Example**

ISO ǥ��, �ҹ���, ���ڸ� ����ϰ�, �ܾ���� `_`�� ����:
> ISO Standard, use lower case only and digits, separate words with underscores:

* `int`
* `vector`
* `my_map`

�� �� ¥�� ���� `__`�� ������� ����(�ݱ�).
> Avoid double underscores `__`.

**Example**

[Stroustrup](http://www.stroustrup.com/Programming/PPP-style.pdf):
ISO ǥ��, �׷��� �빮�ڴ� ����ڸ��� Ÿ�԰� ���信�� ���:
> ISO Standard, but with upper case used for your own types and concepts:

* `int`
* `vector`
* `My_map`

**��**
> **Example**

��Ÿǥ���(CamelCase): ���� �ܾ�ε� �ĺ��ڿ��� �ܾ��� ù ���ڸ� �빮�ڷ� �Ѵ�.
> CamelCase: capitalize each word in a multi-word identifier:

* `int`
* `vector`
* `MyMap`
* `myMap`

� ��Ģ�� ù ���ڸ� �ҹ��ڷ� �ϰ�, � ���� ���� �ʴ´�.
> Some conventions capitalize the first letter, some don't.

**�������**
**Note**

������� ��� ���� �ĺ����� ���̸� �ϰ��ǰ� �õ�:
> Try to be consistent in your use of acronyms, lengths of identifiers:

    int mtbf {12};
    int mean_time_between_failor {12};		// �������� ������ // make up your mind

**���� �ϱ�**
> **Enforcement**

�پ��� ��Ģ�� ����� ���̺귯���� ����� ���� ����� ������ ���̴�.
> Would be possible except for the use of libraries with varying conventions.

### <a name="Rl-all-caps"></a> NL 9: ��ũ�� ��Ī���� ��ü �빮�ڸ� ����϶�.
>### <a name="Rl-all-caps"></a> NL 9: Use `ALL_CAPS` for macro names only

##### Reason

������ Ÿ�� ��Ģ�� ��Ű�� �̸��� ���ؼ��� ��ũ�ο� ȥ������ �ʵ��� �ϱ� ����.
>To avoid confusing macros from names that obeys scope and type rules.

##### Example

    void f()
    {
        const int SIZE{1000};  // Bad, use 'size' instead
        int v[SIZE];
    }

##### Note

�� ��Ģ�� ��ũ�ΰ� �ƴ� ������� ����ȴ�.
>This rule applies to non-macro symbolic constants:

    enum bad { BAD, WORSE, HORRIBLE }; // BAD

##### Enforcement

* �ҹ��ڷ� �� ��ũ�δ� ǥ���϶�.
* ��ũ�ΰ� �ƴѵ� �빮�ڷ� �� ���� ǥ���϶�.

>* Flag macros with lower-case letters
>* Flag `ALL_CAPS` non-macro names

### <a name="Rl-camel"></a> NL.10: ī�����̽��� ���϶�.
>### <a name="Rl-camel"></a> NL.10: Avoid CamelCase

##### Reason

�̸��� �����ϱ� ���� `_`�� ����ϴ� ���� ���� C/C++ ��Ÿ���̰� C++ ǥ�� ���̺귯������ ����ϰ� �ִ�.
ī�����̽��� �����Ѵٸ� ���� ���� �߿��� �� ������ �����϶�.
>The use of underscores to separate parts of a name is the original C and C++ style and used in the C++ standard library.
If you prefer CamelCase, you have to choose among different flavors of camelCase.

##### Note

�� ��Ģ�� �ϴ� ī�����̽��� ���ڴٰ� ������ �⺻ ��Ģ�̴�.
ī�����̽��� �� ���ٸ� [consistency](#Rl-name)�� ���ǵ� ��Ÿ���� ����� �Ѵ�.
�ϰ��� ������ ������ ��ȣ���� �켱�Ѵ�.
>This rule is a default to use only if you have a choice.
Often, you don't have a choice and must follow an established style for [consistency](#Rl-name).
The need for consistency beats personal taste.

##### Example

[Stroustrup](http://www.stroustrup.com/Programming/PPP-style.pdf):
����� ���� Ÿ��, ���信 ���� �빮�ڸ� ����ϴ� ISO ǥ��
>ISO Standard, but with upper case used for your own types and concepts:

* `int`
* `vector`
* `My_map`

##### Enforcement

�Ұ����ϴ�.
>Impossible.

### <a name="Rl-space"></a> NL.15: �����̽��� �Ʋ��� ����϶�.
>### <a name="Rl-space"></a> NL.15: Use spaces sparingly

##### Reason

�ʹ� ���� �����̽��� �ڵ带 ��� �길�ϰ� ����� ������.
>Too much space makes the text larger and distracts.

##### Example, bad

    #include < map >

    int main (int argc, char * argv [ ])
    {
        // ...
    }

##### Example

    #include<map>

    int main(int argc, char* argv[])
    {
        // ...
    }

##### Note

��� IDE�� �׵鸸�� Ȯ�ſ� ���� �߰����� �����̽��� ����Ѵ�.
>Some IDEs have their own opinions and add distracting space.

##### Note

�� ������ �����̽��� ������ ��� ���� ������ �ȴ�. �����ϰ� ������ ����.
>We value well-placed whitespace as a significant help for readability. Just don't overdo it.

### <a name="Rl-order"></a> NL.16: �Ϲ����� Ŭ���� �ɹ� ���� ������ ���Ѷ�.
>### <a name="Rl-order"></a> NL.16: Use a conventional class member declaration order

##### Reason

��� ���� ������ �������� �����ش�.
>A conventional order of members improves readability.

Ŭ���� ����� ���� ������ ����϶�.
>When declaring a class use the following order

* Ÿ��: class, enum, alias (`using`����)
* ������, ���� ������, ������.
* �Լ�
* ������

>* types: classes, enums, and aliases (`using`)
* constructors, assignments, destructor
* functions
* data

`private`, `protected`, `public`������ �����϶�.
>Use the `public` before `protected` before `private` order.

����� Ÿ�԰� �Լ��� ����� ������ ������ �д�.
>Private types and functions can be placed with private data.

##### Example

    ???

##### Enforcement

���ȵ� ������ �ٸ��� ǥ�ø� �ض�. �� ��Ģ�� ������ �ʴ� ���� �ڵ尡 ���� ��������.
>Flag departures from the suggested order. There will be a lot of old code that doesn't follow this rule.

### <a name="Rl-knr"></a> NL.17: K&R ����� ���̾ƿ��� ����϶�.
>### <a name="Rl-knr"></a> NL.17: Use K&R-derived layout

##### Reason

�� ����� ���� C/C++ ���̾ƿ��̴�. �������� ��ġ�� �����ǰ� �Լ��� Ŭ���� ���� ��� ��Ҹ� �����ϱⰡ ����.
>This is the original C and C++ layout. It preserves vertical space well. It distinguishes different language constructs (such as functions and classes well).

##### Note

C++������ "Stroustrup" ��Ÿ���̶�� �θ���.
>In the context of C++, this style is often called "Stroustrup".

##### Example

    struct Cable {
        int x;
        // ...
    };

    double foo(int x)
    {
        if (0 < x) {
            // ...
        }

        switch (x) {
            case 0:
                // ...
                break;
            case amazing:
                // ...
                break;
            default:
                // ...
                break;
        }

        if (0 < x)
            ++x;

        if (x < 0)
            something();
        else
            something_else();

        return some_value;
    }

**Note** `if`�� `(`���̿� �����̽��� ��ĭ �ִ´�.
>**Note** a space between `if` and `(`

##### Note

`if`��, `for`���� ������ ���� ������ ����϶�.
>Use separate lines for each statement, the branches of an `if`, and the body of a `for`.

##### Note

`class`�� `struct`�� `{`�� �� �������� ���̰�, �Լ��� `{`�� ���� ���ο� �д�.
>The `{` for a `class` and a `struct` in *not* on a separate line, but the `{` for a function is.

##### Note

ǥ�ض��̺귯�� Ÿ�԰� �����ϱ� ���� ����� ���� Ÿ���� �빮�ڷ� �̸��� ���´�.
>Capitalize the names of your user-defined types to distinguish them from standards-library types.

##### Note

�Լ� �̸����� �빮�ڸ� ���� ����.
>Do not capitalize function names.

##### Enforcement

�̰� �����Ϸ���, IDE�� �ٽ� ������ �����.
>If you want enforcement, use an IDE to reformat.

### <a name="Rl-ptr"></a> NL.18: C++ ��Ÿ���� ���� ����� ����϶�.
>### <a name="Rl-ptr"></a> NL.18: Use C++-style declarator layout

##### Reason

C ��Ÿ���� ���� ����� ����İ� �������� ����ϴµ� ������ �дٸ�, C++ ��Ÿ���� Ÿ���� �����Ѵ�.
���𿡼� ���� ���ڴ� ������ ������ �ʵ��� �Ѵ�.
>The C-style layout emphasizes use in expressions and grammar, whereas the C++-style emphasizes types.
The use in expressions argument doesn't hold for references.

##### Example

    T& operator[](size_t);	// OK
    T &operator[](size_t);	// just strange
    T & operator[](size_t);	// undecided

##### Enforcement

���������� ���� �Ұ���.
>Impossible in the face of history.

### <a name="Rl-void"></a> NL.25: ���� Ÿ������ `void`�� ������� ����.
>### <a name="Rl-void"></a> NL.25: Don't use `void` as an argument type

##### Reason

���� ���� C ȣȯ�� ������ ���� �ʿ��ϱ⿡.
>It's verbose and only needed where C compatibility matters.

##### Example

    void f(void);   // bad

    void g();       // better

###### Note

���Ͻ� ��ġ�� `void f(void)`�� abomination �����ߴ�.
�Լ� �������̽��� �幰�� ������ ��� C���� �׷� abomination�� ���ؼ� ���ڸ� �߰��� �� �ִ�.
>Even Dennis Ritchie deemed `void f(void)` an abomination.
You can make an argument for that abomination in C when function prototypes were rare so that banning:

    int f();
    f(1, 2, "weird but valid C89");   // hope that f() is defined int f(a, b, c) char* c; { /* ... */ }

�߿��� ������ �߱��� ���ε� ���� C�� C++���� ���� �������� �ʴ´�.
>would have caused major problems, but not in the 21st century and in C++.
