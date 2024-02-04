# Usando Resolver em Angular para pré-carregar dados antes de ativar uma rota

O arquivo `resolver.ts` em um projeto Angular é uma parte de uma estratégia chamada "resolver" que é usada para pré-carregar dados antes de ativar uma rota. Um Resolver Angular é uma classe que implementa a interface `Resolve` e é responsável por carregar dados necessários antes que uma rota seja ativada.

Quando uma rota é acionada, o Resolver é chamado para buscar os dados necessários antes que a rota seja ativada. Isso é útil quando você precisa garantir que determinados dados estejam disponíveis antes que a visão associada à rota seja carregada.

Aqui está um exemplo básico de como um Resolver pode ser usado:

```typescript
// user.resolver.ts

import { Injectable } from '@angular/core';
import { Resolve, ActivatedRouteSnapshot, RouterStateSnapshot } from '@angular/router';
import { Observable } from 'rxjs';
import { UserService } from './user.service';

@Injectable({
  providedIn: 'root',
})
export class UserResolver implements Resolve<any> {
  constructor(private userService: UserService) {}

  resolve(route: ActivatedRouteSnapshot, state: RouterStateSnapshot): Observable<any> {
    // Aqui, você chamaria um serviço para buscar dados antes de ativar a rota
    return this.userService.getUser(route.params.id);
  }
}
```

No exemplo acima, `UserResolver` é um Resolver que usa o serviço `UserService` para buscar dados do usuário antes de ativar a rota. Em seguida, você pode associar esse Resolver a uma rota específica no roteador Angular.

Isso ajuda a garantir que os dados estejam disponíveis antes que a visão seja renderizada, evitando flashes de conteúdo vazio e melhorando a experiência do usuário.

Aqui está um outro exemplo de como você pode usar um resolver em Angular. Vamos supor que temos uma rota que exibe detalhes de um usuário e queremos carregar os dados desse usuário antes que a rota seja ativada:

1. **Criar um Resolver:**
   ```typescript
   // user-resolver.service.ts
   import { Injectable } from '@angular/core';
   import { Resolve, ActivatedRouteSnapshot } from '@angular/router';
   import { UserService } from './user.service'; // Suponha que você tenha um serviço para buscar dados de usuários

   @Injectable({
     providedIn: 'root',
   })
   export class UserResolver implements Resolve<any> {
     constructor(private userService: UserService) {}

     resolve(route: ActivatedRouteSnapshot) {
       const userId = route.params['id']; // Obtemos o ID do parâmetro da rota

       // Usamos o serviço para buscar os dados do usuário pelo ID
       return this.userService.getUserById(userId);
     }
   }
   ```

2. **Atualizar as Rotas:**
   ```typescript
   // app-routing.module.ts
   import { NgModule } from '@angular/core';
   import { RouterModule, Routes } from '@angular/router';
   import { UserDetailsComponent } from './user-details/user-details.component';
   import { UserResolver } from './user-resolver.service';

   const routes: Routes = [
     {
       path: 'users/:id',
       component: UserDetailsComponent,
       resolve: {
         userData: UserResolver,
       },
     },
   ];

   @NgModule({
     imports: [RouterModule.forRoot(routes)],
     exports: [RouterModule],
   })
   export class AppRoutingModule {}
   ```

3. **Usar Dados no Componente:**
   ```typescript
   // user-details.component.ts
   import { Component } from '@angular/core';
   import { ActivatedRoute } from '@angular/router';

   @Component({
     selector: 'app-user-details',
     template: `
       <div *ngIf="user">
         <h2>{{ user.name }}</h2>
         <p>Email: {{ user.email }}</p>
         <!-- Outras informações do usuário -->
       </div>
     `,
   })
   export class UserDetailsComponent {
     user: any; // Supondo que esteja usando um objeto para representar um usuário

     constructor(private route: ActivatedRoute) {
       this.user = this.route.snapshot.data['userData'];
     }
   }
   ```

Neste exemplo, o resolver (`UserResolver`) pega o ID do usuário da rota e usa um serviço (`UserService`) para buscar os dados do usuário correspondente. Esses dados são então disponibilizados como `'userData'` no objeto de dados de rota.

Ao navegar para a rota `'users/:id'`, o Angular automaticamente executa o resolver antes de ativar a rota. O componente (`UserDetailsComponent`) pode acessar os dados do usuário pré-carregados diretamente do objeto `ActivatedRoute`.