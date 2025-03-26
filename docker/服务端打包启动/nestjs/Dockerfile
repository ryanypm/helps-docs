# Builder stage 使用 node:20-alpine 镜像
FROM node:20-alpine AS builder

# 工作目录
WORKDIR /app

# 复制 package.json 和 package-lock.json
COPY package*.json ./

# 安装依赖
RUN npm install --registry=https://registry.npmmirror.com

# 复制所有文件
COPY . .

# 生成 prisma client (如果使用的是 prisma的话)
RUN npx prisma generate

# 构建应用
RUN npm run build

# Production stage 使用 node:20-alpine 镜像
FROM node:20-alpine

# 工作目录
WORKDIR /app

# 复制构建文件
COPY --from=builder /app/package*.json ./
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/prisma ./prisma
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/.env.production ./.env.production

# 暴露端口
EXPOSE 3000

# 启动命令
CMD ["npm", "run", "start:prod"]