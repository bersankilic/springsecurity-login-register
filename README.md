# Custom Login Application

Bu proje, Spring Boot ve Spring Security kullanarak basit bir kullanıcı kayıt ve giriş sistemi uygulaması geliştirmektedir. Aşağıda, projede kullanılan sınıfların açıklamaları yer almaktadır.

# Sınıfların Açıklaması

## UserDto.java
**Amaç:** Kullanıcıdan alınan verileri taşımak için kullanılan bir Data Transfer Object (DTO) sınıfıdır.

**Alanlar:**
- `username`
- `password`
- `fullname`

**Metotlar:**
- Getter ve Setter metotları

## User.java
**Amaç:** Veritabanında kullanıcı bilgilerini saklamak için kullanılan bir model sınıfıdır.

**Alanlar:**
- `id`
- `username`
- `password`
- `fullname`

**Metotlar:**
- Constructor
- Getter ve Setter metotları

**Özellikler:**
- `@Entity` anotasyonu ile JPA tarafından bir veritabanı tablosu olarak tanımlanır.

## UserRepository.java
**Amaç:** Kullanıcı verilerini veritabanından almak ve kaydetmek için kullanılan bir repository arayüzüdür.

**Metotlar:**
- `findByUsername(String username)` - Kullanıcı adını kullanarak kullanıcıyı bulur.

**Özellikler:**
- `JpaRepository` arayüzünü genişleterek temel CRUD işlemlerini sağlar.

## CustomUserDetailsServices.java
**Amaç:** Spring Security için kullanıcı detaylarını yükleyen bir servis sınıfıdır.

**Metotlar:**
- `loadUserByUsername(String username)` - Kullanıcı adını kullanarak kullanıcıyı yükler ve doğrular.
- `authorities()` - Kullanıcıya atanmış yetkileri döner.

**Özellikler:**
- `UserDetailsService` arayüzünü uygular ve `@Service` anotasyonu ile bir Spring servisi olarak tanımlanır.

## UserService.java
**Amaç:** Kullanıcı işlemleri için bir servis arayüzüdür.

**Metotlar:**
- `findByUsername(String username)` - Kullanıcı adını kullanarak kullanıcıyı bulur.
- `save(UserDto userDto)` - Kullanıcıyı kaydeder.

## UserServiceImpl.java
**Amaç:** `UserService` arayüzünü uygulayan ve kullanıcı işlemlerini gerçekleştiren bir servis sınıfıdır.

**Alanlar:**
- `PasswordEncoder`
- `UserRepository`

**Metotlar:**
- `findByUsername(String username)` - Kullanıcı adını kullanarak kullanıcıyı bulur.
- `save(UserDto userDto)` - Kullanıcıyı şifreleyerek kaydeder.

**Özellikler:**
- `@Service` anotasyonu ile bir Spring servisi olarak tanımlanır.

## UserController.java
**Amaç:** Kullanıcı kayıt ve giriş işlemlerini yöneten bir denetleyici sınıfıdır.

**Metotlar:**
- `showRegistrationForm()` - Kayıt formunu görüntüler.
- `registerUserAccount()` - Kullanıcı kayıt işlemini gerçekleştirir.
- `showLoginForm()` - Giriş formunu görüntüler.

**Özellikler:**
- `@Controller` anotasyonu ile bir Spring MVC denetleyicisi olarak tanımlanır.

## CustomUserDetails.java
**Amaç:** Spring Security için kullanıcı detaylarını sağlayan bir sınıftır.

**Alanlar:**
- `username`
- `password`
- `authorities`

**Metotlar:**
- `getUsername()` - Kullanıcı adını döner.
- `getPassword()` - Kullanıcı şifresini döner.
- `getAuthorities()` - Kullanıcı yetkilerini döner.

**Özellikler:**
- `UserDetails` arayüzünü uygular.

## SecurityConfig.java
**Amaç:** Uygulamanın güvenlik yapılandırmasını sağlayan bir sınıftır.

**Metotlar:**
- `passwordEncoder()` - Şifreleme işlemi için bir `PasswordEncoder` bean'i oluşturur.
- `securityFilterChain()` - HTTP güvenlik yapılandırmasını sağlar.
- `configureGlobal()` - Kullanıcı detay servisini ve şifreleyiciyi yapılandırır.

**Özellikler:**
- `@Configuration` ve `@EnableWebSecurity` anotasyonları ile bir güvenlik yapılandırma sınıfı olarak tanımlanır.

## register.html
**Amaç:** Kullanıcı kayıt formunu içeren bir HTML şablon dosyasıdır.

**Özellikler:**
- Form alanları: `fullname`, `username`, `password`
- Başarılı kayıt mesajı ve hata mesajları
- CSS stilleri ile sayfa düzeni ve görünümü

## home.html
Amaç: Kullanıcı giriş yaptıktan sonra görüntülenen ana sayfa şablonudur.


## login.html
Amaç: Kullanıcıların giriş yapmasını sağlayan formu içeren HTML şablon dosyasıdır.
Özellikler:
Kullanıcı adı ve şifre alanlarını içeren bir giriş formu.
Kullanıcıların kayıt sayfasına yönlendirilmesi için bir bağlantı.

## application.properties
**Amaç:** Uygulama yapılandırma ayarlarını içeren bir dosyadır.

**Özellikler:**
- Veritabanı bağlantı bilgileri
- JPA ayarları
- Thymeleaf ayarları


