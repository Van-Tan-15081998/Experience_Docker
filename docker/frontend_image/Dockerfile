# Sử dụng hình ảnh Node.js làm hình ảnh cơ sở
FROM node:latest

# Thiết lập thư mục làm việc trong container
WORKDIR /app

# Sao chép mã nguồn của ứng dụng Vue.js vào container
#COPY . .

# Cài đặt các gói cần thiết cho ứng dụng
#RUN npm install
RUN npm add -g @vue/cli @vue/cli-init

# Mở cổng 3000 để ứng dụng Vue.js chạy trên
ENV HOST 0.0.0.0
EXPOSE 3000

# Lệnh mặc định khi container khởi chạy
#CMD ["npm", "run", "serve"]