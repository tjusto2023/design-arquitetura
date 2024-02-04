O Skeleton Loader, também conhecido como Placeholder ou Shimmer, é uma técnica utilizada para melhorar a experiência do usuário enquanto os dados reais estão sendo carregados em uma aplicação web. Aqui estão alguns benefícios de usar um Skeleton Loader:

1. **Melhora a Percepção de Desempenho:**
   - O Skeleton Loader cria a ilusão de carregamento rápido, proporcionando aos usuários a sensação de que algo está acontecendo na interface, mesmo durante o carregamento real dos dados. Isso ajuda a melhorar a percepção de desempenho da aplicação.

2. **Experiência do Usuário Contínua:**
   - Evita que os usuários vejam abruptamente mudanças na interface à medida que os elementos são carregados. O Skeleton fornece uma transição suave entre o estado vazio ou carregando e o estado final da página.

3. **Redução da Sensação de Espera:**
   - Durante o carregamento de dados assíncronos, os usuários podem sentir que estão esperando por informações. O Skeleton ajuda a minimizar essa sensação, mantendo os usuários envolvidos visualmente.

4. **Indicação Clara de Conteúdo:**
   - O Skeleton Loader fornece uma representação visual aproximada do layout e da estrutura dos dados reais que serão exibidos. Isso ajuda os usuários a entenderem o tipo de conteúdo que esperam.

5. **Acessibilidade:**
   - Pode melhorar a acessibilidade, uma vez que oferece uma representação visual clara da estrutura da página. Usuários com deficiência visual ou tecnologias assistivas podem se beneficiar dessa indicação estrutural.

6. **Ferramenta de Design:**
   - Durante o design e desenvolvimento, os Skeleton Loaders podem servir como ferramentas visuais úteis para os designers e desenvolvedores, ajudando a planejar o layout da página antes mesmo da integração dos dados reais.

7. **Fácil Implementação:**
   - Pode ser implementado de maneira relativamente simples, geralmente usando CSS e animações. Frameworks e bibliotecas também oferecem suporte integrado para Skeleton Loaders.

8. **Prevenção de Layout Shifts:**
   - Evita deslocamentos repentinos e desconcertantes de layout à medida que os elementos reais são carregados, garantindo que a página não pisque ou se mova de maneira inesperada.

Lembre-se de que o Skeleton Loader é uma técnica que deve ser usada com moderação e aplicada de forma contextual. Em alguns casos, especialmente para carregamentos rápidos, pode não ser necessário. Entretanto, em situações em que os dados demoram a carregar, o Skeleton Loader pode proporcionar uma experiência de usuário mais agradável.

A combinação de Skeleton Loader e interceptors no Angular pode ser uma abordagem eficaz para melhorar a experiência do usuário durante o carregamento de dados assíncronos. Aqui estão os passos gerais para implementar essa combinação:

## **Criação de um Interceptor**

- Utilize o Angular `HttpInterceptor` para interceptar as solicitações HTTP antes de serem enviadas ao servidor.

```typescript
// skeleton-interceptor.ts

import { Injectable } from '@angular/core';
import {
  HttpEvent,
  HttpHandler,
  HttpInterceptor,
  HttpRequest,
} from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable()
export class SkeletonInterceptor implements HttpInterceptor {
  intercept(
    req: HttpRequest<any>,
    next: HttpHandler
  ): Observable<HttpEvent<any>> {
    // Adicione lógica para exibir o Skeleton Loader aqui

    // Continue com a solicitação original
    return next.handle(req);
  }
}
```

### 2. **Registro do Interceptor:**
   - Registre o interceptor no módulo ou serviço apropriado.

```typescript
// app.module.ts

import { NgModule } from '@angular/core';
import { HTTP_INTERCEPTORS } from '@angular/common/http';
import { SkeletonInterceptor } from './skeleton-interceptor';

@NgModule({
  // ... outras configurações
  providers: [
    {
      provide: HTTP_INTERCEPTORS,
      useClass: SkeletonInterceptor,
      multi: true,
    },
  ],
})
export class AppModule {}
```

### 3. **Exibição do Skeleton Loader:**
   - Adicione lógica no `SkeletonInterceptor` para exibir o Skeleton Loader enquanto os dados estão sendo carregados.

```typescript
// skeleton-interceptor.ts

import { Injectable } from '@angular/core';
import {
  HttpEvent,
  HttpHandler,
  HttpInterceptor,
  HttpRequest,
} from '@angular/common/http';
import { Observable } from 'rxjs';
import { finalize } from 'rxjs/operators';
import { SkeletonService } from './skeleton.service'; // Crie um serviço para gerenciar o estado do Skeleton Loader

@Injectable()
export class SkeletonInterceptor implements HttpInterceptor {
  constructor(private skeletonService: SkeletonService) {}

  intercept(
    req: HttpRequest<any>,
    next: HttpHandler
  ): Observable<HttpEvent<any>> {
    // Exibe o Skeleton Loader
    this.skeletonService.showSkeleton();

    // Continue com a solicitação original
    return next.handle(req).pipe(
      // Esconde o Skeleton Loader após a conclusão da solicitação
      finalize(() => this.skeletonService.hideSkeleton())
    );
  }
}
```

### 4. **Criação do Serviço Skeleton:**
   - Crie um serviço para gerenciar o estado do Skeleton Loader.

```typescript
// skeleton.service.ts

import { Injectable } from '@angular/core';
import { BehaviorSubject } from 'rxjs';

@Injectable({
  providedIn: 'root',
})
export class SkeletonService {
  private skeletonVisible = new BehaviorSubject<boolean>(false);

  skeletonVisible$ = this.skeletonVisible.asObservable();

  showSkeleton() {
    this.skeletonVisible.next(true);
  }

  hideSkeleton() {
    this.skeletonVisible.next(false);
  }
}
```

### 5. **Integração com o Componente:**
   - Integre o estado do Skeleton Loader com os componentes que desejam exibi-lo.

```typescript
// exemplo.component.ts

import { Component, OnInit } from '@angular/core';
import { SkeletonService } from './skeleton.service';

@Component({
  selector: 'app-exemplo',
  templateUrl: './exemplo.component.html',
  styleUrls: ['./exemplo.component.css'],
})
export class ExemploComponent implements OnInit {
  skeletonVisible: boolean;

  constructor(private skeletonService: SkeletonService) {}

  ngOnInit() {
    this.skeletonService.skeletonVisible$.subscribe(
      (visible) => (this.skeletonVisible = visible)
    );
  }
}
```

### 6. **Exibição Condicional no Template:**
   - No template do componente, use a diretiva `*ngIf` para exibir condicionalmente o Skeleton Loader.

```html
<!-- exemplo.component.html -->

<div *ngIf="skeletonVisible; else content">
  <!-- Exibe o Skeleton Loader -->
  <app-skeleton-loader></app-skeleton-loader>
</div>

<ng-template #content>
  <!-- Exibe o conteúdo real quando não estiver carregando -->
  <!-- ... conteúdo real aqui ... -->
</ng-template>
```

Certifique-se de ajustar os detalhes conforme necessário para se adequar à estrutura específica do seu projeto. Essa abordagem cria uma transição suave, mostrando o Skeleton Loader enquanto os dados são carregados e ocultando-o quando

## Injetando dinamicamente

Para injetar dinamicamente o componente `app-skeleton-loader` em um local específico sem definir no template do componente, você pode usar o `ViewContainerRef` e o `ComponentFactoryResolver` fornecidos pelo Angular. Isso permite criar componentes programaticamente. Aqui estão os passos básicos:

1. **Crie um componente dinâmico:**
   - Crie um componente dinâmico que representará o `app-skeleton-loader`.

```typescript
// skeleton-loader.component.ts

import { Component } from '@angular/core';

@Component({
  selector: 'app-skeleton-loader',
  template: '<div>Seu conteúdo do Skeleton Loader aqui</div>',
})
export class SkeletonLoaderComponent {}
```

2. **Crie um serviço para gerenciar a injeção dinâmica:**
   - Crie um serviço que contenha métodos para adicionar/remover o componente dinâmico.

```typescript
// skeleton-injector.service.ts

import { ApplicationRef, ComponentFactoryResolver, ComponentRef, EmbeddedViewRef, Injectable, Injector } from '@angular/core';
import { SkeletonLoaderComponent } from './skeleton-loader.component';

@Injectable({
  providedIn: 'root',
})
export class SkeletonInjectorService {
  private componentRef: ComponentRef<SkeletonLoaderComponent>;

  constructor(
    private componentFactoryResolver: ComponentFactoryResolver,
    private appRef: ApplicationRef,
    private injector: Injector
  ) {}

  // Método para adicionar o componente dinamicamente
  addSkeletonLoader() {
    // Cria um componente dinâmico
    const factory = this.componentFactoryResolver.resolveComponentFactory(SkeletonLoaderComponent);
    this.componentRef = factory.create(this.injector);

    // Adiciona o componente à árvore de visualização
    this.appRef.attachView(this.componentRef.hostView);

    // Obtém o elemento nativo do componente
    const domElem = (this.componentRef.hostView as EmbeddedViewRef<any>).rootNodes[0] as HTMLElement;

    // Adiciona o elemento ao corpo do documento ou a outro local desejado
    document.body.appendChild(domElem);
  }

  // Método para remover o componente
  removeSkeletonLoader() {
    if (this.componentRef) {
      this.appRef.detachView(this.componentRef.hostView);
      this.componentRef.destroy();
    }
  }
}
```

3. **Uso no componente que deseja injetar dinamicamente:**
   - No componente onde você deseja injetar dinamicamente o `app-skeleton-loader`, injete o serviço e use os métodos apropriados.

```typescript
// exemplo.component.ts

import { Component, OnDestroy } from '@angular/core';
import { SkeletonInjectorService } from './skeleton-injector.service';

@Component({
  selector: 'app-exemplo',
  template: '<div (click)="toggleSkeleton()">Clique para alternar o Skeleton Loader</div>',
})
export class ExemploComponent implements OnDestroy {
  private skeletonVisible = false;

  constructor(private skeletonInjectorService: SkeletonInjectorService) {}

  toggleSkeleton() {
    if (this.skeletonVisible) {
      this.skeletonInjectorService.removeSkeletonLoader();
    } else {
      this.skeletonInjectorService.addSkeletonLoader();
    }

    this.skeletonVisible = !this.skeletonVisible;
  }

  ngOnDestroy() {
    // Certifique-se de remover o componente ao destruir o componente atual
    this.skeletonInjectorService.removeSkeletonLoader();
  }
}
```

Este exemplo usa um serviço para gerenciar a adição/remoção do componente dinâmico. O método `addSkeletonLoader` cria dinamicamente o componente `app-skeleton-loader` e o adiciona ao corpo do documento. O método `removeSkeletonLoader` remove o componente quando necessário.

Certifique-se de adaptar esses exemplos conforme necessário para atender aos requisitos específicos do seu projeto.

## Usando como diretiva

Se você deseja converter o `app-skeleton-loader` em uma diretiva, você pode seguir um caminho semelhante. Vou criar um exemplo onde a diretiva pode ser aplicada a qualquer elemento para exibir o efeito de `skeleton-loader`. Aqui estão os passos:

1. **Crie uma diretiva para o Skeleton Loader:**
   - Crie uma diretiva chamada `skeleton-loader.directive.ts` que adiciona o efeito do `skeleton-loader` ao elemento ao qual é aplicado.

```typescript
// skeleton-loader.directive.ts

import { Directive, ElementRef, Renderer2, Input } from '@angular/core';

@Directive({
  selector: '[appSkeletonLoader]',
})
export class SkeletonLoaderDirective {
  @Input() set appSkeletonLoader(visible: boolean) {
    if (visible) {
      this.showSkeletonLoader();
    } else {
      this.hideSkeletonLoader();
    }
  }

  constructor(private el: ElementRef, private renderer: Renderer2) {}

  private showSkeletonLoader() {
    // Adicione lógica para exibir o efeito do skeleton-loader no elemento
    this.renderer.addClass(this.el.nativeElement, 'skeleton-loader');
  }

  private hideSkeletonLoader() {
    // Adicione lógica para remover o efeito do skeleton-loader no elemento
    this.renderer.removeClass(this.el.nativeElement, 'skeleton-loader');
  }
}
```

2. **Estilo CSS para o Skeleton Loader:**
   - Crie um estilo CSS para o efeito do `skeleton-loader`. Este exemplo usa uma animação simples de fundo de gradiente para simular o efeito.

```css
/* Adicione isso ao seu estilo global ou onde for apropriado */
.skeleton-loader {
  background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
  background-size: 200% 100%;
  animation: loading 1.5s infinite;
}

@keyframes loading {
  0% {
    background-position: -200% 0;
  }
  100% {
    background-position: 200% 0;
  }
}
```

3. **Uso da Diretiva no Componente:**
   - No componente onde deseja usar a diretiva, aplique a diretiva a um elemento e controle sua visibilidade dinamicamente.

```html
<!-- exemplo.component.html -->

<div [appSkeletonLoader]="skeletonVisible" (click)="toggleSkeleton()">Clique para alternar o Skeleton Loader</div>
```

```typescript
// exemplo.component.ts

import { Component } from '@angular/core';

@Component({
  selector: 'app-exemplo',
  template: '<div [appSkeletonLoader]="skeletonVisible" (click)="toggleSkeleton()">Clique para alternar o Skeleton Loader</div>',
  styles: [`
    /* Adicione o estilo específico para o seu componente, se necessário */
  `],
})
export class ExemploComponent {
  skeletonVisible = false;

  toggleSkeleton() {
    this.skeletonVisible = !this.skeletonVisible;
  }
}
```

Este exemplo usa uma diretiva para aplicar e remover dinamicamente o efeito do `skeleton-loader` com base em uma propriedade booleana (`skeletonVisible`). Ao clicar no elemento, você pode alternar a visibilidade do `skeleton-loader`. Certifique-se de adaptar o código conforme necessário para atender aos requisitos específicos do seu projeto.