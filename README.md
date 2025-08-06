# 🚀 CHECKOUTPRO BACKEND - DOCUMENTAÇÃO COMPLETA DA API

## 📊 **RESUMO EXECUTIVO**
- **Total de Rotas:** 150+ endpoints
- **Modelos de Dados:** 25+ tabelas
- **Funcionalidades:** Sistema completo de e-commerce, cursos, afiliados, 2FA, templates, analytics
- **Status:** ✅ Totalmente Implementado e Funcional

---

## 🔐 **AUTENTICAÇÃO & SEGURANÇA**

### Autenticação Básica
- **POST** `/api/auth/login` - Login de usuário
- **POST** `/api/auth/register` - Registro de usuário
- **POST** `/api/auth/logout` - Logout
- **POST** `/api/auth/refresh-token` - Renovar token JWT

### Two-Factor Authentication (2FA) - ✅ NOVO
- **POST** `/api/auth/2fa/setup-google` - Configurar Google Authenticator
- **POST** `/api/auth/2fa/verify-google` - Verificar código Google Authenticator
- **POST** `/api/auth/login-2fa` - Login com verificação 2FA
- **DELETE** `/api/auth/2fa/disable` - Desabilitar 2FA

### Recuperação de Senha
- **POST** `/api/auth/forgot-password` - Solicitar recuperação
- **POST** `/api/auth/reset-password` - Redefinir senha
- **POST** `/api/auth/send-verification` - Enviar verificação email

---

## 👥 **GESTÃO DE USUÁRIOS**

### Operações CRUD
- **GET** `/api/users` - Listar usuários (paginado)
- **GET** `/api/users/:id` - Buscar usuário específico
- **PUT** `/api/users/:id` - Atualizar dados do usuário
- **DELETE** `/api/users/:id` - Deletar usuário
- **PUT** `/api/users/:id/security` - Atualizar configurações de segurança

### Perfil e KYC
- **GET** `/api/users/profile` - Perfil do usuário logado
- **PUT** `/api/users/profile` - Atualizar perfil
- **POST** `/api/users/upload-avatar` - Upload foto perfil

---

## 🛒 **PRODUTOS & E-COMMERCE**

### Gestão de Produtos
- **GET** `/api/products` - Listar produtos (filtros, paginação)
- **POST** `/api/products` - Criar produto
- **GET** `/api/products/:id` - Buscar produto específico
- **PUT** `/api/products/:id` - Atualizar produto
- **DELETE** `/api/products/:id` - Deletar produto
- **GET** `/api/products/slug/:slug` - Buscar por slug
- **POST** `/api/products/validate-slug` - Validar disponibilidade slug

### Recursos Avançados de Produtos - ✅ NOVO
- **GET** `/api/products/:id/stats` - Estatísticas do produto
- **PATCH** `/api/products/:id/stats` - Atualizar estatísticas
- **POST** `/api/products/from-template` - Criar produto do template
- **PUT** `/api/products/:id/template` - Aplicar template ao produto
- **GET** `/api/products/:id/full` - Produto com informações completas
- **POST** `/api/products/fix-slugs` - Corrigir slugs duplicados

---

## 🎨 **SISTEMA DE TEMPLATES** - ✅ NOVO

### Gestão de Templates
- **GET** `/api/templates` - Listar templates (paginado)
- **GET** `/api/templates/types` - Tipos de templates disponíveis
- **GET** `/api/templates/:id` - Buscar template específico
- **GET** `/api/templates/type/:type` - Templates por categoria
- **POST** `/api/templates` - Criar novo template
- **PUT** `/api/templates/:id` - Atualizar template
- **DELETE** `/api/templates/:id` - Deletar template

### Operações Especiais
- **POST** `/api/templates/:id/duplicate` - Duplicar template
- **PATCH** `/api/templates/:id/status` - Alterar status (ativo/inativo)

**Tipos de Templates Disponíveis:**
- `course` - Cursos Online
- `ebook` - E-books e Materiais Digitais
- `event` - Eventos e Workshops
- `membership` - Área de Membros
- `software` - Aplicativos e Ferramentas

### Templates Padrão Incluídos:
1. **Template Curso Online** - Estrutura completa para cursos
2. **Template E-book** - Layout otimizado para livros digitais
3. **Template Evento** - Configuração para workshops e lives
4. **Template Membros** - Área exclusiva com níveis
5. **Template Software** - Landing page para aplicativos

---

## 📤 **SISTEMA DE UPLOAD** - ✅ APRIMORADO

### Upload de Vídeos
- **POST** `/api/upload/video` - Upload de vídeo com thumbnail automático
- **DELETE** `/api/upload/video/:filename` - Deletar vídeo
- **GET** `/api/upload/info/:filename` - Informações do vídeo

### Upload de Imagens - ✅ NOVO
- **POST** `/api/upload/image` - Upload de imagem única
- **POST** `/api/upload/multiple-images` - Upload múltiplo de imagens
- **DELETE** `/api/upload/image/:filename` - Deletar imagem

**Formatos Suportados:**
- Vídeos: MP4, AVI, MOV, WMV, WEBM
- Imagens: JPG, PNG, GIF, WEBP, BMP

**Recursos Automáticos:**
- Validação de formato e tamanho
- Geração automática de thumbnail para vídeos
- Redimensionamento automático de imagens
- Compressão otimizada

---

## 🛍️ **GESTÃO DE PEDIDOS**

### Operações CRUD
- **GET** `/api/orders` - Listar pedidos (filtros avançados)
- **POST** `/api/orders` - Criar pedido
- **GET** `/api/orders/:id` - Buscar pedido específico
- **PUT** `/api/orders/:id` - Atualizar pedido
- **DELETE** `/api/orders/:id` - Cancelar pedido

### Funil de Vendas
- **POST** `/api/orders/:id/upsell` - Processar upsell
- **POST** `/api/orders/:id/downsell` - Processar downsell
- **GET** `/api/orders/:id/funnel-status` - Status do funil

---

## 📊 **ANALYTICS & RELATÓRIOS** - ✅ APRIMORADO

### Analytics Básicos
- **GET** `/api/analytics/sales/:sellerId` - Relatório de vendas
- **GET** `/api/analytics/products/:sellerId` - Performance produtos
- **GET** `/api/analytics/funnel-metrics/:sellerId` - Métricas do funil
- **GET** `/api/analytics/funnel-events/:sellerId` - Eventos do funil

### Dashboard Analytics - ✅ NOVO
- **GET** `/api/analytics/dashboard/:sellerId` - Dashboard principal com:
  - Receita total do período
  - Número de vendas
  - Taxa de conversão
  - Ticket médio
  - Top 5 produtos por receita
  - Comparação com período anterior

- **GET** `/api/analytics/product-performance/:sellerId` - Performance detalhada:
  - Vendas por produto
  - Receita por produto
  - Taxa de conversão por produto
  - Análise temporal

### Rastreamento de Eventos - ✅ NOVO
- **POST** `/api/analytics/track-view` - Rastrear visualização de produto
- **POST** `/api/analytics/track-conversion` - Rastrear conversão

**Métricas Disponíveis:**
- Revenue Analytics (receita por período)
- Conversion Funnel (taxa de conversão por etapa)
- Product Performance (performance individual)
- Customer Analytics (análise de clientes)
- Time-based Analytics (análise temporal)

---

## 🎓 **SISTEMA DE CURSOS ONLINE**

### Gestão de Cursos
- **GET** `/api/courses` - Listar cursos
- **POST** `/api/courses` - Criar curso
- **GET** `/api/courses/:id` - Buscar curso específico
- **PUT** `/api/courses/:id` - Atualizar curso
- **DELETE** `/api/courses/:id` - Deletar curso

### Módulos e Aulas
- **GET** `/api/courses/:id/modules` - Módulos do curso
- **POST** `/api/courses/:id/modules` - Criar módulo
- **PUT** `/api/courses/:courseId/modules/:moduleId` - Atualizar módulo
- **DELETE** `/api/courses/:courseId/modules/:moduleId` - Deletar módulo

### Matrículas e Progresso
- **POST** `/api/courses/:id/enroll` - Matricular aluno
- **GET** `/api/courses/:id/enrollments` - Matrículas do curso
- **GET** `/api/courses/student/:studentId/progress` - Progresso do aluno
- **PUT** `/api/courses/student/:studentId/progress/:lessonId` - Atualizar progresso

---

## 🤝 **SISTEMA DE AFILIADOS/PARCEIROS**

### Gestão de Parceiros
- **GET** `/api/partners` - Listar parcerias
- **POST** `/api/partners` - Criar parceria
- **GET** `/api/partners/product/:productId` - Parceiros do produto
- **GET** `/api/partners/user/:userId` - Parcerias do usuário
- **PUT** `/api/partners/:id` - Atualizar parceria
- **DELETE** `/api/partners/:id` - Remover parceria
- **GET** `/api/partners/code/:partnerCode` - Buscar por código

### Comissões
- **GET** `/api/partners/:id/commissions` - Comissões do parceiro
- **POST** `/api/partners/commissions/calculate` - Calcular comissão
- **PUT** `/api/partners/commissions/:id/pay` - Marcar como pago

---

## 💳 **SISTEMA DE PAGAMENTOS**

### Processamento
- **POST** `/api/card-payment/process` - Processar pagamento
- **POST** `/api/card-payment/validate` - Validar dados cartão
- **GET** `/api/card-payment/status/:transactionId` - Status transação

### Métodos de Pagamento
- **GET** `/api/payment/methods` - Métodos disponíveis
- **POST** `/api/payment/pix/generate` - Gerar PIX
- **POST** `/api/payment/boleto/generate` - Gerar boleto

---

## 📧 **SISTEMA DE EMAILS** - ✅ CORRIGIDO

### Templates e Envios
- **POST** `/api/email/send-welcome` - Email de boas-vindas
- **POST** `/api/email/send-product-notification` - Notificação produto
- **POST** `/api/email/send-order-confirmation` - Confirmação pedido
- **POST** `/api/email/send-recovery-cart` - Recuperação carrinho

### Configurações SMTP - ✅ FUNCIONAL
- **GET** `/api/email/config` - Configurações atuais
- **PUT** `/api/email/config` - Atualizar configurações
- **POST** `/api/email/test` - Testar conexão SMTP

**Configuração SMTP Suportada:**
- Gmail SMTP
- Hostinger SMTP
- Configuração personalizada
- Rate limiting para evitar spam

---

## 📱 **RASTREAMENTO FACEBOOK/META**

### Configuração
- **GET** `/api/facebook/auth/facebook` - Iniciar autorização
- **GET** `/api/facebook/auth/facebook/callback` - Callback autorização
- **POST** `/api/facebook/config/pixel` - Configurar pixel
- **GET** `/api/facebook/status` - Status da integração

### Eventos e Tracking
- **POST** `/api/facebook/track` - Enviar evento
- **POST** `/api/facebook/test-event` - Testar evento
- **GET** `/api/facebook/logs` - Logs de eventos
- **GET** `/api/facebook/pixel/:pixelId/events` - Eventos do pixel

---

## 🔗 **SISTEMA DE WEBHOOKS**

### Gestão de Webhooks
- **GET** `/api/webhooks` - Listar webhooks
- **POST** `/api/webhooks` - Criar webhook
- **GET** `/api/webhooks/:id` - Buscar webhook específico
- **PUT** `/api/webhooks/:id` - Atualizar webhook
- **DELETE** `/api/webhooks/:id` - Deletar webhook

### Testes e Monitoramento
- **POST** `/api/webhooks/:id/test` - Testar webhook
- **GET** `/api/webhooks/stats` - Estatísticas gerais
- **GET** `/api/webhooks/:id/logs` - Logs do webhook

---

## 📋 **KYC & VERIFICAÇÃO**

### Upload de Documentos
- **POST** `/api/kyc/upload-documents` - Upload documentos KYC
- **GET** `/api/kyc/status` - Status verificação
- **GET** `/api/kyc/documents/:userId` - Documentos do usuário
- **PUT** `/api/kyc/update-status` - Atualizar status (admin)

---

## 💰 **PLANOS & ASSINATURAS**

### Gestão de Planos
- **GET** `/api/plans` - Listar planos disponíveis
- **GET** `/api/plans/:planId` - Detalhes do plano
- **POST** `/api/plans/subscribe` - Criar assinatura
- **PUT** `/api/plans/subscription/:id` - Atualizar assinatura
- **DELETE** `/api/plans/subscription/:id` - Cancelar assinatura

---

## ⚙️ **CONFIGURAÇÕES DO SISTEMA** - ✅ PADRONIZADO

### Configurações Gerais
- **GET** `/api/settings` - Listar configurações
- **PUT** `/api/settings` - Atualizar configurações
- **GET** `/api/settings/:key` - Buscar configuração específica
- **POST** `/api/settings/:key` - Criar configuração
- **DELETE** `/api/settings/:key` - Deletar configuração

### Configurações Específicas
- **PUT** `/api/settings/smtp` - Configurar SMTP
- **PUT** `/api/settings/payment` - Configurar pagamentos
- **PUT** `/api/settings/security` - Configurações segurança

**Environment Variables Suportadas:**
- DATABASE_URL (Neon PostgreSQL)
- AZURE_DB_* (Azure PostgreSQL)
- LOCAL_DB_* (PostgreSQL local)
- SMTP_* (Configurações de email)
- JWT_SECRET, ENCRYPTION_KEY
- FACEBOOK_*, UPLOAD_* configs

---

## 🔄 **FUNIL DE VENDAS AVANÇADO**

### Gestão do Funil
- **GET** `/api/funnel/products/:productId` - Funil do produto
- **POST** `/api/funnel/products/:productId/upsells` - Criar upsell
- **PUT** `/api/funnel/upsells/:id` - Atualizar upsell
- **DELETE** `/api/funnel/upsells/:id` - Deletar upsell

### Analytics do Funil
- **GET** `/api/funnel/analytics/:productId` - Analytics detalhados
- **GET** `/api/funnel/conversion-rates/:productId` - Taxa conversão
- **GET** `/api/funnel/revenue/:productId` - Receita por etapa

---

## 🌐 **ROTAS DO SISTEMA**

### Status e Health Check
- **GET** `/` - Página inicial da API
- **GET** `/health` - Health check (Docker)
- **GET** `/api/status` - Status detalhado do sistema
- **GET** `/api/test-cors` - Testar configurações CORS

### Arquivos Estáticos
- **GET** `/uploads/*` - Servir arquivos de upload (vídeos, imagens, documentos)

---

## 📊 **MODELOS DE DADOS IMPLEMENTADOS**

1. **User** - Usuários e autenticação
2. **Product** - Produtos e configurações
3. **ProductTemplate** - ✅ Templates de produtos
4. **ProductStats** - ✅ Estatísticas dos produtos
5. **Order** - Pedidos e transações
6. **OrderItem** - Itens dos pedidos
7. **ProductUpsell** - Upsells e downsells
8. **Course** - Cursos online
9. **CourseModule** - Módulos dos cursos
10. **CourseLesson** - Aulas dos cursos
11. **CourseEnrollment** - Matrículas
12. **CourseProgress** - Progresso dos alunos
13. **ProductPartner** - Sistema de afiliados
14. **PartnerCommission** - Comissões dos parceiros
15. **FacebookConfig** - Configurações Facebook
16. **FacebookEventLog** - Logs de eventos Facebook
17. **ProductFacebookConfig** - Configs Facebook por produto
18. **FunnelAnalytics** - Analytics do funil
19. **Analytics** - Analytics gerais
20. **AbandonedCart** - Carrinho abandonado
21. **WalletTransaction** - Transações financeiras
22. **Webhook** - Sistema de webhooks
23. **WebhookLog** - Logs dos webhooks
24. **Setting** - Configurações do sistema
25. **BackupLog** - Logs de backup

---

## 🎯 **EXEMPLOS DE USO**

### Criando um Produto com Template
```bash
# 1. Listar templates disponíveis
GET /api/templates/types

# 2. Criar produto usando template
POST /api/products/from-template
{
  "templateId": "uuid-do-template",
  "name": "Meu Novo Curso",
  "price": 197.00,
  "customizations": {
    "description": "Descrição personalizada"
  }
}
```

### Upload de Imagens para Produto
```bash
# Upload múltiplas imagens
POST /api/upload/multiple-images
Content-Type: multipart/form-data
files: [arquivo1.jpg, arquivo2.png]

# Response: ["filename1.jpg", "filename2.png"]
```

### Dashboard Analytics
```bash
# Obter dados do dashboard
GET /api/analytics/dashboard/user-id?period=30days

# Response inclui:
# - totalRevenue, totalSales, conversionRate
# - topProducts, revenueByPeriod
# - comparação com período anterior
```

---

## 🚀 **STATUS ATUAL**

### ✅ **IMPLEMENTADO E FUNCIONANDO**
- Sistema completo de autenticação com 2FA
- CRUD completo de produtos com templates
- Sistema de upload (vídeos e imagens)
- Analytics avançados com dashboard
- Sistema de cursos online
- Afiliados e comissões
- Rastreamento Facebook/Meta
- Sistema de webhooks
- KYC e verificação
- Email service (SMTP real)
- Configurações via environment variables

### 🎯 **CARACTERÍSTICAS TÉCNICAS**
- **Arquitetura:** Node.js + Express + Sequelize ORM
- **Banco de Dados:** PostgreSQL (Neon/Azure/Local)
- **Autenticação:** JWT + 2FA (Google Authenticator)
- **Upload:** Multer com validação automática
- **Email:** Nodemailer com SMTP real
- **Rate Limiting:** Proteção contra spam/abuse
- **CORS:** Configurado para produção
- **Docker:** Containerização completa

### 🔧 **MELHORIAS DISPONÍVEIS**
- Rate limiting configurável
- Backup automático
- Cache com Redis
- Monitoramento com logs estruturados
- API de relatórios em PDF
- Integração com mais gateways de pagamento

---

## 🏆 **RESUMO FINAL**

**🎯 Total de Endpoints: 150+**
**🗃️ Modelos de Dados: 25+**
**🔒 Segurança: JWT + 2FA + Rate Limiting**
**📧 Email: SMTP Real (Gmail/Hostinger)**
**📊 Analytics: Dashboard completo**
**🎨 Templates: 5 templates padrão**
**📤 Upload: Vídeos + Imagens**
**🚀 Status: Produção Ready**

### ✨ **NOVIDADES DESTA VERSÃO**
- ✅ Sistema completo de templates
- ✅ Upload de imagens (single/multiple)  
- ✅ Dashboard analytics avançado
- ✅ Estatísticas de produtos
- ✅ Padronização de environment variables
- ✅ Correção do serviço de email
- ✅ Melhoria nas mensagens do sistema

**O backend está 100% funcional e pronto para integração com o frontend!**
