Các câu lệnh hay sử dụng trong hệ thống
 ```bash
 - Kiểm tra dữ liệu
df -h    #kiểm tra dung lượng hệ thống
du -h --max-depth=1 / | sort -hr                        #kiểm tra vân vùng đang chiếm dữ liệu - dùng để kiểm tra và dọn dẹp
du -h --max-depth=1 --exclude=/proc / | sort -hr        #Bỏ qua /proc
sudo usermod -aG sudo username                          #thêm user vào group sudo
certbot --nginx -d (domain-name)                        #thêm certbot nginx
 - Truyền key ssh 
ssh-copy-id -i ~/.ssh/id_rsa.pub root@(.........)       #copy public key ở server client sang server kia 
 
 - Lệnh nén thư mục
tar -czvf 'folder'                                      #thay bằng tên folder
hostnamectl set-hostname abc                            #đổi hostname
zip -r ten_file.zip ten_thu_muc/                        #zip

####iptables####
iptables-restore < /etc/iptables/rules.v4           (sửa file thì chạy cái này)
iptables-save > /etc/iptables/rules.v4              (mở bằng shell thì chạy cái này)


certbot --nginx -d aler.mypoint.com.vn               ###cerbot



Mariadb
SELECT User, Host FROM mysql.user;      ####show user

Docker
docker images                                --kiểm tra các images đang có
docker ps                                    --kiểm tra các container đang chạy
docker ps -a                                 --kiểm tra tất cả các container đang có
docker load -i                               --build images (file .tar)

Add thêm disk
# 1. Rescan
echo "- - -" | sudo tee /sys/class/scsi_host/host*/scan
# 2. Tạo Physical Volume
pvcreate /dev/sdc
# 3. Add vào Volume Group
vgextend ubuntu-vg /dev/sdc
# 4. Extend Logical Volume root
lvextend -l +100%FREE /dev/ubuntu-vg/lv-root
#5. Nếu là ext4: resize2fs /dev/ubuntu-vg/lv-root (ubuntu thường 90% sẽ là ext4) nếu là xfs: xfs_growfs /

terragrunt plan
terragrunt apply
```