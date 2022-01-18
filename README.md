{{ define "main" }}

  {{ if .Content }}
  <section class="section text-center pb-0">
    <div class="container">
    {{ .Content }}
      dvdf
    </div>
  </section>
  {{ end }}
  {{ "<!-- topics -->" | safeHTML }}
  <section class="section">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-12 text-center">
          <h2 class="section-title">{{ i18n "topics_title" | safeHTML }}</h2>
        </div>
        {{ "<!-- topic-item -->" | safeHTML }}
        {{ range (where .Site.Pages "Type" "docs") }}
        <div class="col-lg-4 col-sm-6 mb-4">
          <a href="{{ .Permalink }}" class="px-4 py-5 bg-white shadow text-center d-block match-height">
            {{ with .Params.icon}}<i class="{{.}} icon text-primary d-block mb-4"></i>{{end}}
            <h3 class="mb-3 mt-0">{{ .Title }}</h3>
            {{with .Params.description}}<p class="mb-0">{{. | markdownify}}</p>{{end}}
          </a>
        </div>
        {{ end }}
      </div>
    </div>
  </section>
  {{ "<!-- /topics -->" | safeHTML }}

  {{ if .Site.Params.cta.enable }}
  {{ with .Site.Params.cta }}
  {{ "<!-- call to action -->" | safeHTML }}
  <section>
    <div class="container">
      <div class="row">
        <div class="col-12">
          <div class="section px-3 bg-white shadow text-center">
          <h2 class="mb-4">{{ .title | markdownify }}</h2>
          <p class="mb-4">{{ .content | markdownify }}</p>
          {{ if .button.enable }}
          {{ with .button }}
          <a href="{{ .link | relLangURL }}" class="btn btn-primary">{{ .label }}</a>
          {{ end }}
          {{ end }}
          </div>
        </div>
      </div>
    </div>
  </section>
  {{ "<!-- /call to action -->" | safeHTML }}
  {{ end }}
  {{ end }}

{{ end }}
