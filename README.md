# AWS Cloud Infrastructure: EC2 Static Web Deployment

Bu proje; bulut bilişim (Cloud Computing) ekosisteminin lideri olan **Amazon Web Services (AWS)** mimarisine giriş yapmak, AWS yönetim konsolu üzerinden sanal sunucu (EC2 Instance) altyapısını ayağa kaldırmak, ağ güvenlik duvarlarını (Security Groups) yönetmek ve canlı bir web sunucusu (Nginx) yapılandırmak amacıyla gerçekleştirilmiştir.

## ️ Altyapı ve Sunucu Özellikleri

* **Cloud Provider:** Amazon Web Services (AWS)
* **Compute Resource:** EC2 (Elastic Compute Cloud)
* **Instance Type:** `t2.micro` (1 vCPU, 1 GB RAM - AWS Free Tier)
* **Operating System (AMI):** Ubuntu Server 24.04 LTS
* **Web Server:** Nginx (Engine-X)
* **Networking:** AWS Default VPC & Subnet with Public IPv4 Allocation

##  Güvenlik Yapılandırması (Security Group)

Sunucu güvenliğini sağlamak ve sadece gerekli portlara izin vermek adına bir AWS Security Group kurgulanmıştır:

| Port | Protokol | Kaynak (Source) | Amaç |
| :--- | :--- | :--- | :--- |
| `22` | SSH | `0.0.0.0/0` (Anywhere) | Güvenli terminal bağlantısı ve anahtar erişimi. |
| `80` | HTTP | `0.0.0.0/0` (Anywhere) | Web sitesinin dünyaya açık yayın yapması. |

---

##  Canlıya Alım ve Deployment Adımları

1. AWS Console üzerinden `RSA` tabanlı `.pem` anahtarı üretildi ve Mac yerelinde yetkileri kısıtlandı (`chmod 400`).
2. `~/.ssh/config` dosyasına `ubuntu` kullanıcısı ve AWS Public IP'si tanımlanarak erişim otomatize edildi.
3. Sunucu içerisine Nginx kuruldu ve varsayılan kök dizin olan `/var/www/html/index.html` adresi özelleştirilmiş HTML mimarisiyle güncellenerek site HTTP protokolü üzerinden tüm dünyaya yayınlandı.

##  Kazanımlar
* **Bulut Altyapı Yönetimi (Cloud IaaS):** Bulut üzerinde kaynak oluşturma, maliyet kontrolü (Free Tier) ve bölge (Region) mantığı.
* **Sanal Ağ ve Güvenlik:** Security Group kuralları ile sunucu düzeyinde network katmanı filtrelemesi.
* **AWS Entegrasyonu:** İlerleyen süreçlerde geliştirilecek olan CI/CD (AWS CodePipeline) ve DNS (Route 53) süreçleri için temel altyapı olgunluğunun kazanılması.


https://roadmap.sh/projects/ec2-instance
