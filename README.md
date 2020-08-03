������ ��ť��Ƽ �⺻ V1
==================

### MySQL DB �� ����� ����

create user 'cos'@'%' identified by 'cos1234';
GRANT ALL PRIVILEGES ON *.* TO 'cos'@'%';
create database security;
use security;

### SecurityConfig.java ���� ���� ���

// protected void configure(HttpSecurity http) �Լ� ���ο� ���� ������
.antMatchers("/admin/**").access("hasRole('ROLE_ADMIN') or hasRole('ROLE_USER')")
.antMatchers("/admin/**").access("hasRole('ROLE_ADMIN') and hasRole('ROLE_USER')")
.antMatchers("/admin/**").access("hasRole('ROLE_ADMIN')")
### ��Ʈ�ѷ��� �Լ��� ���� ���� ���� �ϴ� ���

// Ư�� �ּ� ���ٽ� ���� �� ������ ���� ������̼� Ȱ��ȭ SecurityConfig.java�� ����
@EnableGlobalMethodSecurity(prePostEnabled = true, securedEnabled = true)

// ��Ʈ�ѷ��� ������̼� �Ŵ� ��
@PostAuthorize("hasRole('ROLE_MANAGER')")
@PreAuthorize("hasRole('ROLE_MANAGER')")
@Secured("ROLE_MANAGER")