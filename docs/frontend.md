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