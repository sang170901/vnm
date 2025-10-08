# 🚀 VNMaterial - Roadmap & Development Plan

**Project**: Website tổng hợp thông tin vật liệu xây dựng Việt Nam  
**Timeline**: 6-8 tuần  
**Tech Stack**: Laravel 11 + Filament 3 + MySQL  
**Budget năm 1**: 5,000k - 6,500k VNĐ

---

## 📊 TÍNH NĂNG CHÍNH

### User Features
- ✅ Đăng ký / Đăng nhập (email + social login)
- ✅ Quản lý profile
- ✅ Nhận voucher giảm giá
- ✅ Đánh giá sản phẩm / nhà cung cấp
- ✅ Wishlist / Favorite

### Product Management
- ✅ CRUD sản phẩm (Create, Read, Update, Delete)
- ✅ Phân loại đa cấp (categories hierarchy)
- ✅ Upload nhiều ảnh / sản phẩm
- ✅ Thuộc tính sản phẩm (màu sắc, kích thước, vật liệu...)
- ✅ Tìm kiếm gần đúng (fuzzy search)
- ✅ Filter & sort nâng cao
- ✅ Trang chi tiết sản phẩm (SEO friendly)

### Supplier Management
- ✅ CRUD nhà cung cấp
- ✅ 1 Supplier → nhiều Products
- ✅ Profile page cho supplier
- ✅ Bài viết liên quan supplier
- ✅ Contact form

### Content Management
- ✅ Slider với scheduling (tự động publish/unpublish)
- ✅ Slider link đến supplier/product
- ✅ Blog posts
- ✅ SEO optimization (meta tags, sitemap)

### Admin Panel
- ✅ Dashboard với thống kê
- ✅ Quản lý users (khóa/mở tài khoản)
- ✅ Quản lý products (thêm/sửa/xóa/ẩn)
- ✅ Quản lý suppliers
- ✅ Quản lý vouchers (code, discount, expiry)
- ✅ Quản lý sliders (upload, schedule, order)
- ✅ Activity logs (ai làm gì, khi nào)
- ✅ Scheduled publishing (hẹn giờ hiển thị)

---

## 🛠️ TECH STACK

### Backend
```yaml
Framework: Laravel 11
Language: PHP 8.3
Database: MySQL 8.0
Cache: Redis
Queue: Laravel Queue Worker
Authentication: Laravel Sanctum
```

### Admin Panel
```yaml
Admin Framework: Filament 3 (open-source)
Dashboard: Built-in widgets & charts
Role Management: Spatie Laravel Permission
File Upload: Filament Media Library
```

### Frontend
```yaml
Template Engine: Blade (Laravel)
JavaScript: Alpine.js (lightweight)
CSS: Current styles.css (keep design)
Icons: FontAwesome 6
```

### Search & Performance
```yaml
Search Engine: Laravel Scout
Search Driver: TNTSearch (hoặc Meilisearch)
Image Optimization: Intervention Image
CDN: Cloudflare (optional)
```

### DevOps
```yaml
Version Control: Git + GitHub
Repository: https://github.com/sang170901/vnm.git
Server: VPS 2GB RAM (Azdigi hoặc Vultr)
Web Server: Nginx
SSL: Let's Encrypt (FREE)
```

---

## 📅 TIMELINE (6 TUẦN)

### Week 1: Setup & Foundation
**Tasks:**
- [ ] Install Laravel 11 + Composer
- [ ] Design database schema (15-20 tables)
- [ ] Create models + migrations
- [ ] Setup authentication (Laravel Breeze)
- [ ] Install Filament 3 admin panel
- [ ] Setup Git repository

**Deliverables:**
- ✅ Laravel project chạy được
- ✅ Admin panel access (/admin)
- ✅ Database schema hoàn chỉnh

---

### Week 2: Core Backend
**Tasks:**
- [ ] Product CRUD (model, controller, routes)
- [ ] Supplier CRUD
- [ ] Category system (nested/hierarchy)
- [ ] Image upload system (multiple images)
- [ ] Product-Supplier relationships (pivot table)
- [ ] Basic RESTful API endpoints

**Deliverables:**
- ✅ API endpoints hoạt động
- ✅ Relationships test passed
- ✅ Sample data seeded

---

### Week 3: Admin Panel & Frontend
**Tasks:**
- [ ] Configure Filament Product resource
- [ ] Configure Filament Supplier resource
- [ ] Configure Filament Category resource
- [ ] Create admin dashboard widgets
- [ ] Migrate current HTML → Blade templates
- [ ] Integrate Alpine.js

**Deliverables:**
- ✅ Admin có thể CRUD data qua UI
- ✅ Frontend hiển thị data động
- ✅ Design giữ nguyên như HTML cũ

---

### Week 4: Advanced Features
**Tasks:**
- [ ] Implement Laravel Scout search
- [ ] Fuzzy search + autocomplete
- [ ] Filter system (price, category, supplier...)
- [ ] Voucher management (CRUD + apply logic)
- [ ] Slider scheduling (start_date, end_date)
- [ ] Product detail page (SEO meta tags)
- [ ] Supplier profile page

**Deliverables:**
- ✅ Search hoạt động tốt
- ✅ Voucher system functional
- ✅ Trang chi tiết responsive + SEO

---

### Week 5: Polish & Testing
**Tasks:**
- [ ] Responsive design (mobile, tablet)
- [ ] Performance optimization (caching, query)
- [ ] Image lazy loading
- [ ] SEO optimization (sitemap.xml, robots.txt)
- [ ] Security hardening (CSRF, XSS, SQL injection)
- [ ] Cross-browser testing
- [ ] Bug fixing

**Deliverables:**
- ✅ Website mượt trên mọi thiết bị
- ✅ PageSpeed score > 85
- ✅ No critical bugs

---

### Week 6: Deployment & Training
**Tasks:**
- [ ] Rent VPS (Azdigi 2GB hoặc Vultr)
- [ ] Install LEMP stack (Linux, Nginx, MySQL, PHP)
- [ ] Configure server (firewall, SSL)
- [ ] Deploy Laravel application
- [ ] Setup 2 domains + SSL certificates
- [ ] Database migration
- [ ] Setup cron jobs (scheduler)
- [ ] Admin training (video recording)
- [ ] Documentation (README, API docs)

**Deliverables:**
- ✅ Website live tại 2 domains
- ✅ HTTPS enabled
- ✅ Admin biết cách quản lý

---

## 💾 DATABASE SCHEMA

### Core Tables
```sql
-- Authentication & Users
users (id, name, email, password, role, phone, avatar, status)
roles (id, name, permissions)
user_vouchers (user_id, voucher_id, used_at)

-- Products
categories (id, name, slug, parent_id, icon, description, order)
products (
    id, name, slug, description, 
    price, discount_price, sku, 
    status, featured, views, 
    created_at, updated_at
)
product_images (id, product_id, image_url, is_primary, order)
product_attributes (id, product_id, attribute_name, attribute_value)
product_categories (product_id, category_id)

-- Suppliers
suppliers (
    id, name, slug, email, phone, 
    address, logo, description, 
    website, status, user_id
)
supplier_products (supplier_id, product_id, price, stock, sku)
supplier_posts (
    id, supplier_id, title, slug, 
    content, image, published_at
)

-- Content Management
sliders (
    id, title, subtitle, image, link, 
    order, start_date, end_date, status
)
posts (
    id, title, slug, content, excerpt, 
    image, category_id, author_id, 
    published_at, views
)
post_categories (id, name, slug, parent_id)

-- Marketing
vouchers (
    id, code, discount_type, discount_value, 
    min_purchase, max_uses, used_count, 
    start_date, end_date, status
)

-- System
activity_logs (
    id, user_id, action, model_type, 
    model_id, changes, ip, created_at
)
```

---

## 💰 NGÂN SÁCH DỰ KIẾN NĂM 1

### Chi phí cố định (Hosting & Domain)
```
📍 HOSTING & INFRASTRUCTURE
├─ 2 Domain .com.vn          : 600k/năm
├─ VPS 2GB RAM (Azdigi)      : 2,400k/năm
├─ SSL Certificate           : FREE (Let's Encrypt)
├─ CDN (Cloudflare)          : FREE
└─ TOTAL HOSTING            : ~3,000k/năm

📦 SERVICES
├─ Email Business            : 1,500k/năm (optional)
├─ Backup Service            : 600k/năm
├─ Monitoring                : FREE (UptimeRobot)
└─ TOTAL SERVICES           : ~2,100k/năm

════════════════════════════════
💰 TỔNG CHI PHÍ NĂM 1: ~5,000k - 6,500k
════════════════════════════════
```

### Development Cost
```
👨‍💻 Development by AI Assistant: FREE
⚠️ Note: Requires your testing & feedback
```

---

## 📦 LARAVEL PACKAGES CẦN DÙNG

```json
{
  "filament/filament": "^3.0",
  "spatie/laravel-permission": "^6.0",
  "spatie/laravel-medialibrary": "^11.0",
  "spatie/laravel-backup": "^9.0",
  "spatie/laravel-sluggable": "^3.0",
  "laravel/scout": "^10.0",
  "teamtnt/laravel-scout-tntsearch-driver": "^14.0",
  "intervention/image": "^3.0",
  "laravel/telescope": "^5.0",
  "laravel/sanctum": "^4.0"
}
```

---

## 🚀 QUICK START COMMANDS

### Setup Laravel (First time)
```powershell
# Check Composer
composer --version

# Create Laravel project
cd c:\xampp\htdocs
composer create-project laravel/laravel vnmt-backend

# Install Filament
cd vnmt-backend
composer require filament/filament:"^3.0"
php artisan filament:install --panels

# Setup database
# Edit .env file with your database config

# Run migrations
php artisan migrate

# Create admin user
php artisan make:filament-user

# Start dev server
php artisan serve
```

### Daily Development
```powershell
# Start Laravel server
php artisan serve

# Run migrations
php artisan migrate

# Create new model
php artisan make:model Product -mfs

# Create Filament resource
php artisan make:filament-resource Product

# Clear cache
php artisan optimize:clear
```

---

## 📝 IMPORTANT NOTES

### Current Status (Ngày 8/10/2025)
- ✅ HTML/CSS frontend hoàn thành
- ✅ GitHub repository connected
- ✅ Design approved (light blue theme)
- ⏳ Backend Laravel chưa bắt đầu

### Next Steps
1. Install Composer (nếu chưa có)
2. Create Laravel project
3. Install Filament admin panel
4. Design database schema
5. Migrate HTML to Blade templates

### Contact & Repository
- **GitHub**: https://github.com/sang170901/vnm.git
- **Branch**: main
- **Last commit**: 33a588b - Initial commit

---

## 🎯 SUCCESS METRICS

### Month 3
- [ ] 100+ sản phẩm
- [ ] 20+ nhà cung cấp
- [ ] Website live & stable

### Month 6
- [ ] 500+ sản phẩm
- [ ] 50+ nhà cung cấp
- [ ] 1,000+ users
- [ ] Search optimization working

### Month 12
- [ ] 2,000+ sản phẩm
- [ ] 100+ nhà cung cấp
- [ ] 10,000+ users
- [ ] Revenue from ads/commissions

---

## 📞 SUPPORT & MAINTENANCE

### Regular Tasks
- Daily: Monitor server uptime
- Weekly: Check error logs
- Monthly: Database backup
- Quarterly: Security updates

### Backup Strategy
- Daily: Database auto-backup
- Weekly: Full backup (code + DB)
- Monthly: Off-site backup

---

**Last updated**: October 8, 2025  
**Status**: Planning Phase  
**Version**: 1.0
