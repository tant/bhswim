
1. Cấu trúc thư mục dự án 

/your-ecommerce-project
  /supabase-docker  <-- Chứa docker của supabase để dùng tạo database và storage
  /apps
    /backend      <-- Dự án MedusaJS
    /frontend     <-- Dự án Astro + React
  /packages
    /ui           <-- Các component React dùng chung
    /config-eslint  <-- Cấu hình ESLint chung
    /config-tsconfig<-- Cấu hình TypeScript chung
  package.json
  pnpm-workspace.yaml
  turbo.json

2. Các bước thiết lập
2.1 Docker lên

2.2 Đảm bảo node và pnpm 
Node.js: Nên dùng phiên bản LTS (v18 hoặc v20 tại thời điểm hiện tại).

pnpm: Trình quản lý package hiệu quả cho monorepo. Cài đặt bằng npm:



npm install -g pnpm