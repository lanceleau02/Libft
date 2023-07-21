<div align="center">

<h1>Libft</h1>

<a href="https://imgflip.com/i/7q0hc7"><img src="https://i.imgflip.com/7q0hc7.jpg" width="350px" title="meme"/></a>
  
<a><img src="https://badge42.vercel.app/api/v2/clj4r0l4t004008mgcfxas4fw/project/2833039" title="score"/></a>
  
</div>

<p>Description:</p>

> Write your own library: a collection of functions that will be a useful tool for your cursus.

<h2>✔️ Project's requirements</h2>

- Declaring global variables is forbidden.
- If you need helper functions to split a more complex function, define them as static
functions. This way, their scope will be limited to the appropriate file.
- Place all your files at the root of your repository.
- Turning in unused files is forbidden.
- Every .c files must compile with the flags -Wall -Wextra -Werror.
- You must use the command ar to create your library. Using the libtool command
is forbidden.
- Your libft.a has to be created at the root of your repository.

<h2>🧬 Theory</h2>

Code the functions.

<h2>📝 Code explanation</h2>

<h3>Mandatory part</h3>

<details>

<summary>isalpha | isdigit | isalnum | isascii | isprint</summary>

<br>

```C
int	ft_isalpha(int c)
{
	if ((c >= 65 && c <= 90) || (c >= 97 && c <= 122))
		return (1);
	return (0);
}
```
```C
int	ft_isdigit(int c)
{
	if (c >= 48 && c <= 57)
		return (1);
	return (0);
}
```
```C
int	ft_isalnum(int c)
{
	if (ft_isalpha(c) || ft_isdigit(c))
		return (1);
	return (0);
}
```
```C
int	ft_isascii(int c)
{
	if (c >= 0 && c <= 127)
		return (1);
	return (0);
}
```
```C
int	ft_isprint(int c)
{
	if (c >= 32 && c <= 126)
		return (1);
	return (0);
}
```

</details>

---

<details>

<summary>strlen</summary>

<br>

```C
size_t	ft_strlen(const char *s)
{
	size_t	i;

	i = 0;
	while (s[i] != '\0')
		i++;
	return (i);
}
```

</details>

---

<details>

<summary>memset</summary>

<br>

```C
void	*ft_memset(void *s, int c, size_t n)
{
	unsigned char	*area;

	area = (unsigned char *)s;
	while (n != 0)
	{
		area[n - 1] = c;
		n--;
	}
	return (s);
}
```

</details>

---

<details>

<summary>bzero</summary>

<br>

```C
void	ft_bzero(void *s, size_t n)
{
	unsigned char	*area;

	area = s;
	while (n != 0)
	{
		area[n - 1] = '\0';
		n--;
	}
}
```

</details>

---

<details>

<summary>memcpy</summary>

<br>

```C
void	*ft_memcpy(void *dest, const void *src, size_t n)
{
	unsigned char	*copy;
	unsigned char	*original;
	size_t			i;

	if (dest == NULL && src == NULL)
		return (NULL);
	copy = (unsigned char *)dest;
	original = (unsigned char *)src;
	i = 0;
	while (i < n)
	{
		copy[i] = original[i];
		i++;
	}
	return (copy);
}
```

</details>

---

<details>

<summary>memmove</summary>

<br>

```C
void	*ft_memmove(void *dest, const void *src, size_t n)
{
	unsigned char	*copy;
	unsigned char	*original;
	int				i;

	if (dest == NULL && src == NULL)
		return (NULL);
	copy = (unsigned char *)dest;
	original = (unsigned char *)src;
	if (copy < original)
		ft_memcpy(copy, original, n);
	else
	{
		i = n - 1;
		while (i >= 0)
		{
			copy[i] = original[i];
			i--;
		}
	}
	return (copy);
}
```

</details>

---

<details>

<summary>strlcpy</summary>

<br>

```C
size_t	ft_strlcpy(char *dst, const char *src, size_t size)
{
	size_t	i;

	if (size == 0)
		return (ft_strlen(src));
	i = 0;
	while (src[i] != '\0' && i < (size - 1))
	{
		dst[i] = src[i];
		i++;
	}
	if (size > 0)
		dst[i] = '\0';
	return (ft_strlen(src));
}
```

</details>

---

<details>

<summary>strlcat</summary>

<br>

```C
size_t	ft_strlcat(char *dst, const char *src, size_t size)
{
	size_t	i;
	size_t	size_dst;
	size_t	size_src;

	if (dst == NULL && size == 0)
		return (ft_strlen(src));
	size_dst = ft_strlen(dst);
	size_src = ft_strlen(src);
	if (size_dst >= size)
		return (size_src + size);
	i = 0;
	while (src[i] != '\0' && (size_dst + i) < (size - 1))
	{
		dst[size_dst + i] = src[i];
		i++;
	}
	dst[size_dst + i] = '\0';
	return (size_dst + size_src);
}
```

</details>

---

<details>

<summary>toupper</summary>

<br>

```C
int	ft_toupper(int c)
{
	if (c >= 97 && c <= 122)
	{
		c -= 32;
		return (c);
	}
	return (c);
}
```

</details>

---

<details>

<summary>tolower</summary>

<br>

```C
int	ft_tolower(int c)
{
	if (c >= 65 && c <= 90)
	{
		c += 32;
		return (c);
	}
	return (c);
}
```

</details>

---

<details>

<summary>strchr</summary>

<br>

```C
char	*ft_strchr(const char *s, int c)
{
	int	i;

	i = 0;
	while (s[i] != (unsigned char)c)
	{
		if (s[i] == '\0')
			return (NULL);
		i++;
	}
	return ((char *)&s[i]);
}
```

</details>

---

<details>

<summary>strrchr</summary>

<br>

```C
char	*ft_strrchr(const char *s, int c)
{
	int	i;

	i = ft_strlen(s);
	while (s[i] != (unsigned char)c && i >= 0)
	{
		if (i == 0)
			return (NULL);
		i--;
	}
	return ((char *)&s[i]);
}
```

</details>

---

<details>

<summary>strncmp</summary>

<br>

```C
int	ft_strncmp(const char *s1, const char *s2, size_t n)
{
	size_t	i;

	if (n == 0)
		return (0);
	i = 0;
	while (s1[i] != '\0' && i < n - 1 && (s1[i] == s2[i]))
		i++;
	return (((unsigned char *)s1)[i] - ((unsigned char *)s2)[i]);
}
```

</details>

---

<details>

<summary>memchr</summary>

<br>

```C
void	*ft_memchr(const void *s, int c, size_t n)
{
	unsigned char	*memblock;
	size_t			i;

	memblock = (unsigned char *)s;
	i = 0;
	while (i < n)
	{
		if (memblock[i] == (unsigned char)c)
			return (&memblock[i]);
		i++;
	}
	return (NULL);
}
```

</details>

---

<details>

<summary>memcmp</summary>

<br>

```C
int	ft_memcmp(const void *s1, const void *s2, size_t n)
{
	unsigned char	*firstblock;
	unsigned char	*secondblock;
	size_t			i;

	firstblock = (unsigned char *)s1;
	secondblock = (unsigned char *)s2;
	i = 0;
	while (i < n)
	{
		if (firstblock[i] != secondblock[i])
			return (firstblock[i] - secondblock[i]);
		i++;
	}
	return (0);
}
```

</details>

---

<details>

<summary>strnstr</summary>

<br>

```C
char	*ft_strnstr(const char *big, const char *little, size_t len)
{
	size_t			i;
	size_t			j;

	if (big == NULL && len == 0)
		return (NULL);
	else if (little[0] == '\0')
		return ((char *)big);
	i = 0;
	while (big[i] != '\0' && i < len)
	{
		j = 0;
		while (i + j < len && big[i + j] == little[j])
		{
			if (little[j + 1] == '\0')
				return ((char *)&big[i]);
			j++;
		}
		i++;
	}
	return (0);
}
```

</details>

---

<details>

<summary>atoi</summary>

<br>

```C
int	ft_atoi(const char *nptr)
{
	int				i;
	int				minus;
	long			nb;

	i = 0;
	while (nptr[i] && ((nptr[i] >= 9 && nptr[i] <= 13) || nptr[i] == ' '))
		i++;
	minus = 1;
	if (nptr[i] == '-' || nptr[i] == '+')
	{
		if (nptr[i] == '-')
			minus *= -1;
		i++;
	}
	nb = 0;
	while (nptr[i] != '\0' && ft_isdigit(nptr[i]) == 1)
	{
		if (nb * minus > 2147483647)
			return (-1);
		if (nb * minus < -2147483648)
			return (0);
		nb = nb * 10 + (nptr[i] - 48);
		i++;
	}
	return (minus * nb);
}
```

</details>

---

<details>

<summary>calloc</summary>

<br>

```C
void	*ft_calloc(size_t nmemb, size_t size)
{
	void	*memblock;

	if ((int)nmemb < 0 && (int)size < 0)
		return (NULL);
	memblock = malloc(sizeof(char) * (nmemb * size));
	if (memblock == NULL)
		return (NULL);
	ft_bzero(memblock, (nmemb * size));
	return (memblock);
}
```

</details>

---

<details>

<summary>strdup</summary>

<br>

```C
char	*ft_strdup(const char *s)
{
	char	*copy;
	int		i;

	copy = malloc(sizeof(char) * ft_strlen(s) + 1);
	if (copy == NULL)
		return (NULL);
	i = 0;
	while (s[i] != '\0')
	{
		copy[i] = s[i];
		i++;
	}
	copy[i] = '\0';
	return (copy);
}
```

</details>

---

<details>

<summary>substr</summary>

<br>

```C
char	*ft_substr(char const *s, unsigned int start, size_t len)
{
	char	*new_s;
	size_t	i;

	if (s == NULL)
		return (NULL);
	else if (start >= ft_strlen(s) || len == 0)
		return (ft_strdup(""));
	i = 0;
	while (s[start + i] != '\0' && i < len)
		i++;
	new_s = malloc(sizeof(char) * (i + 1));
	if (new_s == NULL)
		return (NULL);
	i = 0;
	while (i < len && s[start] != '\0')
	{
		new_s[i] = s[start];
		i++;
		start++;
	}
	new_s[i] = '\0';
	return (new_s);
}
```

</details>

---

<details>

<summary>strjoin</summary>

<br>

```C
char	*ft_strjoin(char const *s1, char const *s2)
{
	char	*new_s;
	int		i;
	int		j;

	if (s1 == NULL || s2 == NULL)
		return (NULL);
	new_s = malloc(sizeof(char) * (ft_strlen(s1) + ft_strlen(s2) + 1));
	if (new_s == NULL)
		return (NULL);
	i = 0;
	while (s1[i] != '\0')
	{
		new_s[i] = s1[i];
		i++;
	}
	j = 0;
	while (s2[j] != '\0')
	{
		new_s[i] = s2[j];
		i++;
		j++;
	}
	new_s[i] = '\0';
	return (new_s);
}
```

</details>

---

<details>

<summary>strtrim</summary>

<br>

```C
static int	ft_checkchar(char const c, char const *set)
{
	int	i;

	if (set == NULL)
		return (0);
	i = 0;
	while (set[i] != '\0')
	{
		if (set[i] == c)
			return (1);
		i++;
	}
	return (0);
}

char	*ft_strtrim(char const *s1, char const *set)
{
	char			*new_s;
	unsigned int	start;
	unsigned int	end;
	size_t			len;

	if (s1 == NULL)
		return (NULL);
	else if (s1[0] == '\0' || set[0] == '\0')
		return (ft_strdup(s1));
	start = 0;
	while (s1[start] != '\0' && ft_checkchar(s1[start], set) == 1)
		start++;
	end = ft_strlen(s1) - 1;
	while (end >= start && ft_checkchar(s1[end], set) == 1)
		end--;
	len = end - start;
	new_s = ft_substr(s1, start, len + 1);
	return (new_s);
}
```

</details>

---

<details>

<summary>split</summary>

<br>

```C
static int	ft_definewordlen(char const *s, char c)
{
	int	i;

	i = 0;
	while (s[i] != '\0' && s[i] != c)
		i++;
	return (i);
}

static int	ft_definewordcount(char const *s, char c)
{
	int	i;
	int	wordcount;

	i = 0;
	wordcount = 0;
	while (s[i] != '\0')
	{
		if ((s[i] == c && s[i + 1] != c && s[i + 1] != '\0') \
		|| (s[0] != c && i == 0))
			wordcount++;
		i++;
	}
	return (wordcount);
}

static void	ft_mfree(char **new_s, int position)
{
	int	i;

	i = 0;
	while (i <= position)
	{
		free(new_s[i]);
		new_s[i] = NULL;
		i++;
	}
}

char	**ft_split(char const *s, char c)
{
	char	**new_s;
	int		i;
	int		j;

	if (s == NULL)
		return (NULL);
	new_s = malloc(sizeof(char *) * (ft_definewordcount(s, c) + 1));
	if (new_s == NULL)
		return (NULL);
	i = 0;
	j = 0;
	while (s[i] != '\0')
	{
		if ((i == 0 && s[i] != c) || (i != 0 && s[i - 1] == c && s[i] != c))
		{
			new_s[j] = ft_substr(s, i, ft_definewordlen(&s[i], c));
			if (new_s[j] == NULL)
				ft_mfree(new_s, j);
			j++;
		}
		i++;
	}
	new_s[j] = NULL;
	return (new_s);
}
```

</details>

---

<details>

<summary>itoa</summary>

<br>

```C
static int	ft_definesize(long n)
{
	int	size;

	size = 0;
	if (n <= 0)
	{
		size++;
		n *= -1;
	}
	while (n > 0)
	{
		n /= 10;
		size++;
	}
	return (size);
}

char	*ft_itoa(int n)
{
	long	nb;
	int		size;
	char	*string;

	nb = (long)n;
	size = ft_definesize(nb);
	string = malloc(sizeof(char) * (size + 1));
	if (string == NULL)
		return (NULL);
	string[size] = '\0';
	if (nb < 0)
	{
		string[0] = '-';
		nb *= -1;
	}
	if (nb == 0)
		string[0] = '0';
	while (nb > 0)
	{
		string[size - 1] = (nb % 10) + 48;
		nb /= 10;
		size--;
	}
	return (string);
}
```

</details>

---

<details>

<summary>strmapi</summary>

<br>

```C
char	*ft_strmapi(char const *s, char (*f)(unsigned int, char))
{
	char	*new_s;
	int		i;

	if (s == NULL)
		return (NULL);
	new_s = malloc(sizeof(char) * ft_strlen(s) + 1);
	if (new_s == NULL)
		return (NULL);
	i = 0;
	while (s[i] != '\0')
	{
		new_s[i] = f(i, s[i]);
		i++;
	}
	new_s[i] = '\0';
	return (new_s);
}
```

</details>

---

<details>

<summary>striteri</summary>

<br>

```C
void	ft_striteri(char *s, void (*f)(unsigned int, char*))
{
	int	i;

	if (s == NULL)
		return ;
	i = 0;
	while (s[i] != '\0')
	{
		f(i, &s[i]);
		i++;
	}
}
```

</details>

---

<details>

<summary>putchar_fd</summary>

<br>

```C
void	ft_putchar_fd(char c, int fd)
{
	write(fd, &c, 1);
}
```

</details>

---

<details>

<summary>putstr_fd</summary>

<br>

```C
void	ft_putstr_fd(char *s, int fd)
{
	int	i;

	if (s == NULL)
		return ;
	i = 0;
	while (s[i] != '\0')
	{
		ft_putchar_fd(s[i], fd);
		i++;
	}
}
```

</details>

---

<details>

<summary>putendl_fd</summary>

<br>

```C
void	ft_putendl_fd(char *s, int fd)
{
	ft_putstr_fd(s, fd);
	ft_putchar_fd('\n', fd);
}
```

</details>

---

<details>

<summary>putnbr_fd</summary>

<br>

```C
void	ft_putnbr_fd(int n, int fd)
{
	if (n == -2147483648)
	{
		ft_putstr_fd("-2147483648", fd);
		return ;
	}
	if (n < 0)
	{
		ft_putchar_fd('-', fd);
		n *= -1;
	}
	if (n >= 10)
	{
		ft_putnbr_fd(n / 10, fd);
		ft_putnbr_fd(n % 10, fd);
	}
	if (n < 10)
		ft_putchar_fd(n + '0', fd);
}
```

</details>

<h3>Bonus part</h3>

<details>

<summary>lstnew</summary>

<br>

```C
t_list	*ft_lstnew(void *content)
{
	t_list	*new;

	new = malloc(sizeof(t_list));
	if (new == NULL)
		return (NULL);
	new->content = content;
	new->next = NULL;
	return (new);
}
```

</details>

---

<details>

<summary>lstadd_front</summary>

<br>

```C
void	ft_lstadd_front(t_list **lst, t_list *new)
{
	if (lst == NULL || new == NULL)
		return ;
	new->next = *lst;
	*lst = new;
}
```

</details>

---

<details>

<summary>lstsize</summary>

<br>

```C
int	ft_lstsize(t_list *lst)
{
	int	i;

	if (lst == NULL)
		return (0);
	i = 0;
	while (lst != NULL)
	{
		i++;
		lst = lst->next;
	}
	return (i);
}
```

</details>

---

<details>

<summary>lstlast</summary>

<br>

```C
t_list	*ft_lstlast(t_list *lst)
{
	if (lst == NULL)
		return (NULL);
	while (lst->next != NULL)
		lst = lst->next;
	return (lst);
}
```

</details>

---

<details>

<summary>lstadd_back</summary>

<br>

```C
void	ft_lstadd_back(t_list **lst, t_list *new)
{
	t_list	*tmp;

	if (lst == NULL || new == NULL)
		return ;
	if (*lst == NULL)
		*lst = new;
	else
	{
		tmp = ft_lstlast(*lst);
		tmp->next = new;
	}
}
```

</details>

---

<details>

<summary>lstdelone</summary>

<br>

```C
void	ft_lstdelone(t_list *lst, void (*del)(void *))
{
	if (lst == NULL || del == NULL)
		return ;
	(*del)(lst->content);
	free(lst);
}
```

</details>

---

<details>

<summary>lstclear</summary>

<br>

```C
void	ft_lstclear(t_list **lst, void (*del)(void *))
{
	t_list	*tmp;

	if (lst == NULL || del == NULL)
		return ;
	while (*lst != NULL)
	{
		tmp = *lst;
		*lst = (*lst)->next;
		ft_lstdelone(tmp, del);
	}
}
```

</details>

---

<details>

<summary>lstiter</summary>

<br>

```C
void	ft_lstiter(t_list *lst, void (*f)(void *))
{
	if (lst == NULL || f == NULL)
		return ;
	while (lst != NULL)
	{
		f(lst->content);
		lst = lst->next;
	}
}
```

</details>

---

<details>

<summary>lstmap</summary>

<br>

```C
t_list	*ft_lstmap(t_list *lst, void *(*f)(void *), void (*del)(void *))
{
	t_list	*head;
	t_list	*new_node;

	if (lst == NULL || f == NULL || del == NULL)
		return (NULL);
	head = NULL;
	while (lst != NULL)
	{
		new_node = ft_lstnew(f(lst->content));
		if (new_node == NULL)
		{
			ft_lstclear(&head, del);
			return (NULL);
		}
		ft_lstadd_back(&head, new_node);
		lst = lst->next;
	}
	return (head);
}
```

</details>

<h2>🧰 Toolbox</h2>

- [libftTester](https://github.com/Tripouille/libftTester)
- [libft-unit-test](https://github.com/alelievr/libft-unit-test)

<h2>📚 Resources</h2>

- [Library Functions Manual](https://man7.org/linux/man-pages/man3/)
