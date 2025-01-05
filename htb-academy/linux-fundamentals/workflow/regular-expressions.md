# Regular Expressions `RegEx`

Can be used to **find and replace text**, **analyze data**, **validate input**, **perform searches**, and more.

A `regular expression` is a sequence of **letters and symbols** that form a **search pattern**.
Additionally, `regular expressions` can be created with patterns called `metacharacters`

`Metacharacters` are **symbols** that define the **search pattern** but have no literal meaning.
These are often found in tools like `grep` or `sed`

---

### Grouping

`RegEx` also allows us to **group the desired search patterns**.

> `RegEx` follows **three different concepts**, distinguished by the **three different brackets: `() [] {}`**

#### Grouping Operators

| **Operators** | **Description** |
| --- | --- |
| `(a)` | **Round brackets** are used to **group parts of a `regex`**. Within the brackets are further parterns which should be processed together. |
| `[a-z]` | **Square brackets** are used to **define character classes**. Inside the brackets are a specified list of characters to search for. |
| `{1,10}` | **Curly brackets** are used to **define quantifiers**. Inside the brackets is a specified number or range that indicates how often a previous pattern should be repeated. |
| `|` | The **OR operator** shows results when one of the two expressions matches |
| `.*` | Similar to the **AND operator** as it shows results only when both expressions are present and match in the specified order. |

#### OR operator

Suppose we're looking for lines containing the word `my` or `false`. To use these operators (with `grep`), we much use the `extended regex` flag, `-E`.

``` sh
$ grep -E "(my|false)" /etc/passwd
> lxd:x:105:65534::/var/lib/lxd/:/bin/false
> pollinate:x:109:1::/var/cache/pollinate:/bin/false
> mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false
```

#### AND operator

``` sh
$ grep -E "(my.*false)" /etc/passwd
> mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false
```

---

# Practice

> All exercises will focus on `/etc/ssh/sshd_config` within the `Pwnbox` instance.

## Exercises:
```
1 	Show all lines that do not contain the # character.
2 	Search for all lines that contain a word that starts with Permit.
3 	Search for all lines that contain a word ending with Authentication.
4 	Search for all lines containing the word Key.
5 	Search for all lines beginning with Password and containing yes.
6 	Search for all lines that end with yes.
```

1. 
``` sh
$ grep -v -E "(^$|^#)" /etc/ssh/sshd_config
> Include /etc/ssh/sshd_config.d/*.conf
> KbdInteractiveAuthentication no
> UsePAM yes
> X11Forwarding yes
> PrintMotd no
> AcceptEnv LANG LC_*
> Subsystem	sftp	/usr/lib/openssh/sftp-server
```
> `-v` exclude matching  
> `-E` extended regex  
> `()` group regex  
> `^$` lines with no characters  
> `^#` lines beginning with `#`

2. asd
