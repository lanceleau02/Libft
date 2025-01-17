<div align="center">

![](https://raw.githubusercontent.com/ayogun/42-project-badges/refs/heads/main/badges/libfte.png)

# **Libft**
  
**This project is about coding a C library.**

</div>

## Features

- Custom library functions (e.g., `ft_strlen`, `ft_strcpy`, `ft_strcmp`).
- Memory management functions (e.g., `ft_bzero`, `ft_calloc`, `ft_memcpy`).
- String manipulation functions (e.g., `ft_strcat`, `ft_strchr`, `ft_strjoin`).
- Character checks functions (e.g., `ft_isalpha`, `ft_isdigit`, `ft_isalnum`).
- Linked lists functions (e.g., `ft_lastadd_back`, `ft_lstiter`, `ft_lstnew`).
- Utility functions (e.g., `ft_atoi`, `ft_itoa`, `ft_putchar_fd`).

## Installation

Since this project is a C library, there’s nothing to install. Simply clone the repository and include the `libft.a` file in your project.

1. Clone the repository:

```bash
git clone https://github.com/lanceleau02/Libft.git
```

2. Navigate to the project directory:

```bash
cd Libft
```

3. Compile the library:

```bash
make
```

Use the `libft.a` file in your own C project by linking it during compilation.

## Usage

1. Include the Libft header:

In your C project, include the `libft.h` header file to access the functions provided by Libft.

```c
#include "libft.h"
```

2. Link the Libft library:

When compiling your C project, link the `libft.a` library by using the `-L` flag to specify the path to `libft.a` and `-lft` to link the library.
For example, if you're using `gcc`, you can compile your project like this:

```bash
gcc -o my_project my_project.c -L./Libft -lft
```

Where:

- `-L./Libft` specifies the directory where `libft.a` is located.
- `-lft` links the Libft library.

3. Use Libft functions:

Once linked, you can use any of the Libft functions in your code.

## License

This project is licensed under the **42 School** License.

- **Educational Use Only**: This project is intended for educational purposes at the 42 School as part of the curriculum.
- **Non-commercial Use**: The code may not be used for commercial purposes or redistributed outside of the 42 School context.
- **No Warranty**: The project is provided "as-is", without any warranty of any kind.

For more details, see the [LICENSE](https://github.com/lanceleau02/Libft/blob/main/LICENSE) file.

## Resources

- [libftTester](https://github.com/Tripouille/libftTester)
- [libft-unit-test](https://github.com/alelievr/libft-unit-test)
- [Library Functions Manual](https://man7.org/linux/man-pages/man3/)
