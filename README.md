<h1 align="center">Hello, I'm Luccas 👋</h1>

###

<div align="center">
  <img height="300" & border_radius=20 src="./129001931.png"  />
</div>

<div align="center">
  <a href="https://www.linkedin.com/feed/?trk=guest_homepage-basic_google-one-tap-submit" target="_blank">
    <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="40" alt="linkedin logo"  />
  </a>
  <a href="lucaspcosa70@gmail.com" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Gmail&logo=gmail&label=&color=D14836&logoColor=white&labelColor=&style=for-the-badge" height="40" alt="gmail logo"  />
  </a>
  <a href="https://www.instagram.com/l1uccas/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Instagram&logo=instagram&label=&color=E4405F&logoColor=white&labelColor=&style=for-the-badge" height="40" alt="instagram logo"  />
  </a>
  <a href="12996100607" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Whatsapp&logo=whatsapp&label=&color=25D366&logoColor=white&labelColor=&style=for-the-badge" height="40" alt="whatsapp logo"  />
  </a>
</div>

<hr/>

<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="40" alt="javascript logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" height="40" alt="typescript logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=react" height="40" alt="react logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bootstrap/bootstrap-original.svg" height="40" alt="bootstrap logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg" height="40" alt="csharp logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/eslint/eslint-original.svg" height="40" alt="eslint logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=github" height="40" alt="github logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=git" height="40" alt="git logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=nextjs" height="40" alt="nextjs logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=nodejs" height="40" alt="nodejs logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=mysql" height="40" alt="mysql logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=postgres" height="40" alt="postgresql logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=py" height="40" alt="python logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=visualstudio" height="40" alt="visualstudio logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=vscode" height="40" alt="vscode logo"  />
  <img width="12" />
  <img src="https://cdn.simpleicons.org/adobephotoshop/31A8FF" height="40" alt="adobephotoshop logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=dotnet" height="40" alt="dot-net logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=prisma" height="40" alt="prisma logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=tailwind" height="40" alt="tailwindcss logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=vercel" height="40" alt="vercel logo"  />
</div>

<hr/>

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=luccas-costa&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=rose_pine&locale=pt-br&hide_border=false&order=1&custom_title=Luccas%20costa" height="150" alt="stats graph"/>
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=luccas-costa&locale=pt-br&hide_title=false&layout=compact&card_width=320&langs_count=5&theme=rose_pine&hide_border=false&order=2&custom_title=Linguagens" height="150" alt="languages graph"  />
</div>

<p>
  public void GerarPdfAnaliseLaudoBonito(int idAnuncio, string codigoValidacao, string nomeArquivo)
{
    try
    {
        System.Net.ServicePointManager.SecurityProtocol = System.Net.SecurityProtocolType.Tls12;
        ServicePointManager.SecurityProtocol = SecurityProtocolType.Tls12;
        AppGenerico db = new AppGenerico();

        // ── 1. IDENTIFICAÇÃO DO USUÁRIO DA SESSÃO ────────────────
        string codigoUsuarioLogado = "5987";
        //if (HttpContext.Current.Session["user"] != null &&
        //    HttpContext.Current.Session["user"].ToString().Length >= 4)
        //{
        //    codigoUsuarioLogado = HttpContext.Current.Session["user"].ToString().Substring(0, 4);
        //}
        //else
        //{
        //    throw new Exception("Sessão do usuário não encontrada ou expirada.");
        //}

        // ── 2. DADOS DO MÉDICO ────────────────────────────────────
        string sqlMedico = $"SELECT * FROM usuarios WHERE codigo = {codigoUsuarioLogado}";
        var listaMedico = db.ListarCadastro<mdUsuario>(sqlMedico);
        if (listaMedico == null || listaMedico.Count == 0)
            throw new Exception("Médico logado não encontrado no banco de dados.");

        var medico = listaMedico[0];
        string crmMedico = !string.IsNullOrEmpty(medico.fonemsn) ? medico.fonemsn : "Não informado";

        // ── 3. DADOS DO ANÚNCIO ───────────────────────────────────
        string sqlAnuncio = $@"
SELECT a.titulo, a.idade, a.sexo, a.medicacoes, a.freqrespiratoria,
       d.historiaclinica, d.procirurgico, d.cirugiasanteriores AS cirurgiasanteriores,
       d.alergias, d.atividadefisica, d.tabagismo, d.etilismo, d.sinaisvitais, d.doencascronicas
FROM anuncios a
INNER JOIN details d ON d.idcadastro = a.details
WHERE a.codigo = {idAnuncio}";

        var listaAnuncio = db.ListarCadastro<mdAnuncios>(sqlAnuncio);
        if (listaAnuncio == null || listaAnuncio.Count == 0)
            throw new Exception("Registro de laudo/anúncio não encontrado.");

        var anuncio = listaAnuncio[0];
        string sexo = anuncio.sexo == 0 ? "Masculino"
                    : anuncio.sexo == 1 ? "Feminino"
                    : "Não informado";

        string dataHoraAtual = DateTime.Now.ToString("dd/MM/yyyy - HH:mm:ss");

        // ── 4. DECODIFICAÇÃO DE DOENÇAS CRÔNICAS ─────────────────
        string doencasDecodificadas = !string.IsNullOrWhiteSpace(anuncio.doencascronicas)
            ? anuncio.doencascronicas.Trim()
            : "Nenhuma informada";

        // ── 5. RESPOSTA DO MÉDICO (TIMELINE) ─────────────────────
        string respostaMedico = "";
        string sqlTimeLine = $@"
SELECT texto FROM timeline
WHERE anuncio = {idAnuncio}
ORDER BY codigo ASC LIMIT 1";

        var listaTimeLine = db.ListarCadastro<mdTimeLine>(sqlTimeLine);
        if (listaTimeLine.Count > 0)
            respostaMedico = listaTimeLine[0].texto;

        respostaMedico = respostaMedico
            .Replace("\r\n", "<br />")
            .Replace("\r", "<br />")
            .Replace("\n", "<br />");

        // ── 6. ASSETS EM BASE64 (Necessário para a API externa ler as imagens) ─
        string backgroundPath = HttpContext.Current.Server.MapPath("~/imagens/BACKGROUDN.png");
        string bgBase64 = "";
        if (File.Exists(backgroundPath))
        {
            byte[] bgBytes = File.ReadAllBytes(backgroundPath);
            bgBase64 = "data:image/png;base64," + Convert.ToBase64String(bgBytes);
        }

        string urlQr = $"https://app.plugsign.com.br/validate/{codigoValidacao}";
        byte[] qrBytes = GerarQrCodeBytes(urlQr, tamanho: 200);
        string qrBase64 = "data:image/png;base64," + Convert.ToBase64String(qrBytes);

        // ── 7. MONTA HTML E CSS DO CORPO ────────────────────────────────
        var html = new StringBuilder();
        html.Append("<!DOCTYPE html>");
        html.Append("<html><head><meta charset='UTF-8' />");
        html.Append("<style>");
        // Removemos as margens nativas da página para o background cobrir a folha A4 por inteiro
        html.Append("@page { margin: 0; } ");
        html.Append("body { font-family: Arial, sans-serif; color: #111; font-size: 11px; margin: 0; ");
        // O padding substitui as antigas margens do Document: Top, Right, Bottom, Left
        html.Append("padding: 85px 65px 130px 65px; box-sizing: border-box; min-height: 100vh; position: relative; ");

        if (!string.IsNullOrEmpty(bgBase64))
        {
            html.Append($"background-image: url('{bgBase64}'); background-size: 100% 100%; background-repeat: no-repeat; ");
            html.Append("-webkit-print-color-adjust: exact; print-color-adjust: exact; "); // Garante a impressão do background
        }
        html.Append("} ");

        html.Append(".header { text-align: center; margin-bottom: 8px; } ");
        html.Append(".header h1 { font-size: 22px; font-weight: bold; margin: 0; text-transform: uppercase; letter-spacing: 1px; } ");
        html.Append(".header p { font-size: 13px; margin: 4px 0 0 0; color: #555; } ");
        html.Append(".content-laudo { line-height: 1.65; } ");

        // CSS do Rodapé modernizado com Flexbox
        html.Append(".footer { position: absolute; bottom: 65px; left: 65px; right: 65px; border-top: 1px solid #000; padding-top: 10px; display: flex; align-items: center; } ");
        html.Append(".footer img { width: 75px; height: 75px; margin-right: 15px; } ");
        html.Append(".footer-text-container { flex-grow: 1; display: flex; flex-direction: column; } ");
        html.Append(".footer-row { display: flex; justify-content: space-between; margin-bottom: 5px; } ");
        html.Append(".footer-title { font-size: 11px; } ");
        html.Append(".footer-date { font-size: 9px; color: #505050; } ");
        html.Append(".footer-signature { font-size: 11px; margin-top: 4px; } ");
        html.Append("</style></head><body>");

        // Conteúdo Principal
        html.Append("<div class='header'>");
        html.Append("<h1>Risco Cirúrgico</h1>");
        html.Append($"<p>{medico.nome} - CRM {crmMedico}</p>");
        html.Append("</div>");

        html.Append("<div class='content-laudo'>");
        html.Append($"<p><strong>Nome:</strong> {anuncio.titulo}</p>");
        html.Append($"<p><strong>Idade:</strong> {anuncio.idade} &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Sexo:</strong> {sexo}</p><br />");
        html.Append($"<p><strong>Procedimento:</strong> {anuncio.procirurgico}</p>");
        html.Append($"<p><strong>História Clínica:</strong> {anuncio.historiaclinica}</p>");
        html.Append($"<p><strong>Cirurgias Anteriores:</strong> {anuncio.cirurgiasanteriores}</p>");
        html.Append($"<p><strong>Alergias:</strong> {anuncio.alergias}</p>");
        html.Append($"<p><strong>Doenças Crônicas:</strong> {doencasDecodificadas}</p>");
        html.Append($"<p><strong>Medicamentos:</strong> {anuncio.medicacoes}</p>");
        html.Append($"<p><strong>Histórico Cardíaco:</strong> {anuncio.freqrespiratoria}</p>");
        html.Append($"<p><strong>Sinais Vitais:</strong> {anuncio.sinaisvitais}</p>");
        html.Append($"<p><strong>Atividade Física:</strong> {anuncio.atividadefisica}</p>");
        html.Append($"<p><strong>Tabagismo:</strong> {anuncio.tabagismo}</p>");
        html.Append($"<p><strong>Etilismo:</strong> {anuncio.etilismo}</p><br />");
        html.Append("<hr style='border: none; border-top: 1px solid #ccc;' /><br />");

        html.Append("<p style='font-size: 11px; line-height: 1.6;'>");
        html.Append($"<strong>Cardiologista</strong><br />{respostaMedico}");
        html.Append("</p>");
        html.Append("</div>");

        // Rodapé HTML (Substituindo o antigo PdfPTable)
        html.Append("<div class='footer'>");
        html.Append($"<img src='{qrBase64}' />");
        html.Append("<div class='footer-text-container'>");
        html.Append("<div class='footer-row'>");
        html.Append("<span class='footer-title'>Laudy - Acesso à sua receita digital via QR Code</span>");
        html.Append($"<span class='footer-date'>Data e hora: {dataHoraAtual} (GMT-3)</span>");
        html.Append("</div>");
        html.Append($"<div class='footer-signature'>Assinado digitalmente por <strong>{medico.nome} - CRM {crmMedico}</strong></div>");
        html.Append("</div>"); // Fecha footer-text-container
        html.Append("</div>"); // Fecha footer

        html.Append("</body></html>");

        // ── 8. MONTA CAMINHO FÍSICO DO ARQUIVO ───────────────────
        string pastaDestino = HttpContext.Current.Server.MapPath("~/imagens/dc/analizes/");
        if (!Directory.Exists(pastaDestino))
            Directory.CreateDirectory(pastaDestino);

        string caminhoCompleto = Path.Combine(pastaDestino, nomeArquivo);

        using (var client = new WebClient())
        {
            client.Encoding = Encoding.UTF8;
            client.Headers.Add(HttpRequestHeader.ContentType, "application/json");

            // Injeta a chave exatamente como o exemplo da documentação deles pede
            client.Headers.Add("X-API-Key", "sk_391be592022a79275fcde8383f2e148adb48fe26");

            var payload = new
            {
                source = html.ToString(),
                format = "A4"
            };

            string jsonPayload = JsonConvert.SerializeObject(payload);

            // Faz o envio dos dados para a API
            byte[] pdfBytes = client.UploadData("https://api.pdfshift.io/v3/convert/pdf", "POST", Encoding.UTF8.GetBytes(jsonPayload));

            // Salva o PDF final gerado no caminho físico
            File.WriteAllBytes(caminhoCompleto, pdfBytes);
        }
    }
    catch (Exception ex)
    {
        throw new Exception($"Erro ao gerar PDF: {ex.Message}", ex);
    }
}
</p>

###
