<template>
    <div class="container">
        <router-link :to="{name: 'home'}" class="navbar-brand">
            Laravel
        </router-link>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <!-- Left Side Of Navbar -->
            <ul class="navbar-nav mr-auto">
                <!--LOGGED USER-->
                <li class="nav-item" v-if="$auth.check(1)" v-for="(route, key) in routes.user" v-bind:key="route.path">
                    <router-link class="nav-link"  :to="{ name : route.path }" :key="key">
                        {{route.name}}
                    </router-link>
                </li>
                <!--LOGGED ADMIN-->
                <li class="nav-item" v-if="$auth.check(2)" v-for="(route, key) in routes.admin" v-bind:key="route.path">
                    <router-link class="nav-link"  :to="{ name : route.path }" :key="key">
                        {{route.name}}
                    </router-link>
                </li>
            </ul>

            <!-- Right Side Of Navbar -->
            <ul class="navbar-nav ml-auto">
                <li class="nav-item" v-if="!$auth.check()" v-for="(route, key) in routes.unlogged" v-bind:key="route.path">
                    <router-link class="nav-link"  :to="{ name : route.path }" :key="key">
                        {{route.name}}
                    </router-link>
                </li>
                <!--LOGOUT-->
                <li class="nav-item dropdown"  v-if="$auth.check()">
                    <a id="navbarDropdown" class="nav-link dropdown-toggle" href="#" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" v-pre>
                       *<span class="caret"></span>
                    </a>

                    <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown">
                        <a class="dropdown-item" href="#" @click.prevent="$auth.logout()">Log Out</a>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>
<script>
  export default {
    data() {
      return {
        routes: {
          // UNLOGGED
          unlogged: [
            {
              name: 'Register',
              path: 'register'
            },
            {
              name: 'Login',
              path: 'login'
            }
          ],
          // LOGGED USER
          user: [
            {
              name: 'Dashboard',
              path: 'dashboard'
            }
          ],
          // LOGGED ADMIN
          admin: [
            {
              name: 'Dashboard',
              path: 'admin.dashboard'
            }
          ]
        }
      }
    },
    mounted() {
      //
    }
  }
</script>
