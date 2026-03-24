# 模块12：Banner 管理

**职责**：首页轮播图的运营管理，支持后台配置图片、跳转链接、排序、上下架

## 能力清单

| # | 能力 | 端 | 描述 |
|---|------|---|------|
| 1 | Banner 展示 | 小程序 | 首页顶部轮播图，自动轮播 |
| 2 | Banner 列表管理 | PC | 查看所有 Banner，支持上下架、排序 |
| 3 | Banner 新建/编辑 | PC | 上传图片、设置跳转链接、排序权重、上下架状态 |
| 4 | Banner 删除 | PC | 删除不需要的 Banner（软删除） |

---

## 业务规则

### Banner 字段

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| 标题 | String | 是 | Banner 标识名称（仅后台显示，方便管理） |
| 图片 | String | 是 | Banner 图片 URL（通过 OSS 上传） |
| 跳转链接 | String | 否 | 点击后跳转的小程序页面路径，为空则不跳转 |
| 排序权重 | Int | 是 | 数值越大越靠前，默认 0 |
| 状态 | Enum | 是 | 已上架 / 已下架，默认已下架 |

### 运营规则

- Banner 图片建议比例：推荐宽高比与首页 hero 区域一致（约 16:9 或根据设计稿）
- 跳转链接支持小程序内页面路径（如 `/pages/product-detail/product-detail?uuid=xxx`），也支持留空不跳转
- 小程序端只展示状态为"已上架"且未删除的 Banner，按排序权重降序
- Banner 至少应有 1 张上架图片，否则小程序端 swiper 区域为空时展示默认占位图

---

## 数据模型

```
model Banner {
  id          Int       @id @default(autoincrement())
  uuid        String    @unique @default(uuid())
  title       String    // Banner 标识名称（后台管理用）
  imageUrl    String    // 图片 URL（OSS）
  linkUrl     String?   // 点击跳转链接（小程序页面路径）
  sortWeight  Int       @default(0)     // 排序权重，越大越靠前
  isActive    Boolean   @default(false) // 是否上架
  createdAt   DateTime  @default(now())
  updatedAt   DateTime  @updatedAt
  deletedAt   DateTime? // 软删除
}
```

---

## 关联页面

| 页面 | 端 | 说明 |
|------|---|------|
| P19-Banner管理页 | PC | Banner 列表 + 新建/编辑弹窗 |
| 首页（index） | 小程序 | 轮播图展示 |

---

## 依赖关系

- **依赖**：OSS 上传服务（图片上传）
- **被依赖**：小程序首页

---

## 待澄清问题

（无）
