Đây là cấu trúc thư mục của astro frontend mà chúng ta sẽ dùng
src/
├── components/
│   ├── common/
│   │   ├── Button.astro
│   │   ├── Header.astro
│   │   └── Footer.astro
│   └── features/
│       ├── product/
│       │   ├── ProductCard.astro
│       │   └── ProductList.astro
│       └── user/
│           ├── Profile.astro
│           └── UserMenu.astro
├── content/
│   └── blog/
│       ├── post-1.md
│       └── post-2.md
├── layouts/
│   ├── BaseLayout.astro
│   └── PostLayout.astro
├── pages/
│   ├── index.astro
│   ├── about.astro
│   └── blog/
│       └── [slug].astro
├── styles/
│   ├── global.css
│   └── variables.css
├── lib/ (hoặc utils/)
│   ├── api.ts
│   ├── date.ts
│   └── constants.ts
└── env.d.ts


Giải thích các thư mục:
src/components/: Chứa các thành phần (components) UI có thể tái sử dụng.
common/: Dành cho các component chung, được sử dụng ở nhiều nơi trong ứng dụng (ví dụ: Button, Header, Footer).
features/: Nhóm các component theo tính năng cụ thể (ví dụ: các component liên quan đến product hoặc user). Điều này giúp dễ dàng quản lý khi dự án lớn dần.
src/content/: Dành cho "Content Collections" của Astro, nơi bạn lưu trữ các tệp tin nội dung như Markdown (.md) hoặc MDX (.mdx).
src/layouts/: Chứa các layout chung cho các trang. Ví dụ, BaseLayout.astro có thể chứa header, footer và cấu trúc HTML cơ bản.
src/pages/: Chứa các trang của website. Astro sử dụng "file-based routing", nghĩa là mỗi tệp .astro trong thư mục này sẽ trở thành một trang trên website của bạn.
src/styles/: Chứa các tệp CSS toàn cục, biến CSS, hoặc các tệp style khác.
src/lib/ (hoặc src/utils/): Dành cho các hàm tiện ích, mã logic không phải là component, các hằng số, hoặc các đoạn mã giao tiếp với API.
src/env.d.ts: Tệp khai báo kiểu cho biến môi trường, giúp TypeScript hiểu được các biến trong import.meta.env.

## Hướng dẫn tích hợp Dark Mode với Flowbite và Tailwind CSS (TailwindCSS v4)

### 1. Kích hoạt Dark Mode với TailwindCSS v4
- TailwindCSS v4 mặc định sử dụng dark mode qua class `dark` mà không cần cấu hình trong file config.
- Bạn chỉ cần sử dụng các class như `dark:bg-gray-800`, `dark:text-white`... trong các component.
- Không cần tạo hoặc chỉnh sửa file `tailwind.config.js` nữa.

### 2. Thêm script chuyển đổi dark mode vào layout
- Thêm đoạn script sau vào phần `<head>` của file `src/layouts/BaseLayout.astro`:
  ```html
  <script>
    if (localStorage.getItem('color-theme') === 'dark' ||
        (!('color-theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
      document.documentElement.classList.add('dark');
    } else {
      document.documentElement.classList.remove('dark');
    }
  </script>
  ```

### 3. Tạo nút chuyển đổi dark mode
- Thêm một nút chuyển đổi vào header hoặc vị trí mong muốn:
  ```html
  <button id="theme-toggle" type="button" class="...">...</button>
  <svg id="theme-toggle-dark-icon" class="hidden ...">...</svg>
  <svg id="theme-toggle-light-icon" class="hidden ...">...</svg>
  ```
- Thêm script xử lý sự kiện click cho nút chuyển đổi:
  ```js
  var themeToggleDarkIcon = document.getElementById('theme-toggle-dark-icon');
  var themeToggleLightIcon = document.getElementById('theme-toggle-light-icon');
  var themeToggleBtn = document.getElementById('theme-toggle');

  // Hiển thị icon phù hợp
  if (localStorage.getItem('color-theme') === 'dark' || (!('color-theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
    themeToggleLightIcon.classList.remove('hidden');
  } else {
    themeToggleDarkIcon.classList.remove('hidden');
  }

  themeToggleBtn.addEventListener('click', function() {
    themeToggleDarkIcon.classList.toggle('hidden');
    themeToggleLightIcon.classList.toggle('hidden');
    if (localStorage.getItem('color-theme')) {
      if (localStorage.getItem('color-theme') === 'light') {
        document.documentElement.classList.add('dark');
        localStorage.setItem('color-theme', 'dark');
      } else {
        document.documentElement.classList.remove('dark');
        localStorage.setItem('color-theme', 'light');
      }
    } else {
      if (document.documentElement.classList.contains('dark')) {
        document.documentElement.classList.remove('dark');
        localStorage.setItem('color-theme', 'light');
      } else {
        document.documentElement.classList.add('dark');
        localStorage.setItem('color-theme', 'dark');
      }
    }
  });
  ```

### 4. Sử dụng các class Tailwind/Flowbite với biến thể `dark:`
- Khi dark mode được bật, các class có tiền tố `dark:` sẽ được áp dụng, ví dụ:
  ```html
  <div class="bg-white dark:bg-gray-800">
    <h1 class="text-gray-900 dark:text-white">Dark mode</h1>
  </div>
  ```

### 5. Kiểm tra hoạt động
- Đảm bảo các thành phần sử dụng class `dark:` và nút chuyển đổi hoạt động đúng.


