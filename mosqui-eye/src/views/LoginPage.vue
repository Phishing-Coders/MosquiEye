<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Login</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <ion-card>
        <ion-card-header>
          <ion-card-title>Welcome to Mosquieye</ion-card-title>
          <ion-card-subtitle>Please sign-in to your account</ion-card-subtitle>
        </ion-card-header>
        <ion-card-content>
          <form @submit.prevent="login">
            <ion-item>
              <ion-label position="floating">Email or Username</ion-label>
              <ion-input 
                type="text" 
                v-model="formData.email" 
                required
                :class="{ 'invalid': validationErrors.email }"
              ></ion-input>
              <div class="error-message" v-if="validationErrors.email">
                {{ validationErrors.email }}
              </div>
            </ion-item>

            <ion-item>
              <ion-label position="floating">Password</ion-label>
              <ion-input 
                type="password" 
                v-model="formData.password"
                required
                :class="{ 'invalid': validationErrors.password }"
              ></ion-input>
              <div class="error-message" v-if="validationErrors.password">
                {{ validationErrors.password }}
              </div>
            </ion-item>

            <ion-item lines="none">
              <ion-checkbox v-model="formData.rememberMe"></ion-checkbox>
              <ion-label class="ion-padding-start">Remember Me</ion-label>
            </ion-item>

            <ion-button 
              expand="block" 
              color="primary" 
              type="submit"
              :disabled="isLoading"
            >
              {{ isLoading ? 'Logging in...' : 'Login' }}
            </ion-button>
          </form>

          <ion-button 
            expand="block" 
            fill="clear" 
            @click="forgotPassword"
          >
            Forgot Password?
          </ion-button>

          <ion-button 
            expand="block" 
            fill="clear" 
            @click="createAccount"
          >
            Create an account
          </ion-button>

          <div class="social-login">
            <ion-row>
              <ion-col size="6">
                <ion-button 
                  expand="block" 
                  fill="clear" 
                  color="primary" 
                  @click="loginWithFacebook"
                >
                  <ion-icon slot="start" :icon="logoFacebook"></ion-icon>
                  Facebook
                </ion-button>
              </ion-col>
              <ion-col size="6">
                <ion-button 
                  expand="block" 
                  fill="clear" 
                  color="primary" 
                  @click="loginWithTwitter"
                >
                  <ion-icon slot="start" :icon="logoTwitter"></ion-icon>
                  Twitter
                </ion-button>
              </ion-col>
            </ion-row>
          </div>
        </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<script>
import { defineComponent, ref } from 'vue';
import { 
  IonPage, 
  IonHeader, 
  IonToolbar, 
  IonTitle,
  IonContent,
  IonCard,
  IonCardHeader,
  IonCardTitle,
  IonCardSubtitle,
  IonCardContent,
  IonItem,
  IonLabel,
  IonInput,
  IonButton,
  IonCheckbox,
  IonRow,
  IonCol,
  IonIcon,
  toastController
} from '@ionic/vue';
import { logoFacebook, logoTwitter } from 'ionicons/icons';
import { useRouter } from 'vue-router';

export default defineComponent({
  name: 'LoginPage',
  components: {
    IonPage,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonCard,
    IonCardHeader,
    IonCardTitle,
    IonCardSubtitle,
    IonCardContent,
    IonItem,
    IonLabel,
    IonInput,
    IonButton,
    IonCheckbox,
    IonRow,
    IonCol,
    IonIcon
  },
  setup() {
    const formData = ref({
      email: '',
      password: '',
      rememberMe: false
    });

    const validationErrors = ref({
      email: '',
      password: ''
    });

    const isLoading = ref(false);
    const router = useRouter();

    const validateForm = () => {
      let isValid = true;
      validationErrors.value = {
        email: '',
        password: ''
      };

      if (!formData.value.email) {
        validationErrors.value.email = 'Email is required';
        isValid = false;
      } else if (!/\S+@\S+\.\S+/.test(formData.value.email)) {
        validationErrors.value.email = 'Please enter a valid email';
        isValid = false;
      }

      if (!formData.value.password) {
        validationErrors.value.password = 'Password is required';
        isValid = false;
      } else if (formData.value.password.length < 6) {
        validationErrors.value.password = 'Password must be at least 6 characters';
        isValid = false;
      }

      return isValid;
    };

    const showToast = async (message, color = 'success') => {
      const toast = await toastController.create({
        message,
        duration: 2000,
        color
      });
      toast.present();
    };

    const login = async () => {
      if (!validateForm()) return;

      try {
        isLoading.value = true;
        // Add your login API call here
        await new Promise(resolve => setTimeout(resolve, 1500)); // Simulating API call
        
        showToast('Login successful!');
        router.push('/SignUpPage');// Handle successful login (e.g., redirect to dashboard)
      } catch (error) {
        showToast(error.message || 'Login failed', 'danger');
      } finally {
        isLoading.value = false;
      }
    };

    const forgotPassword = () => {
      // Navigate to forgot password page
      console.log('Navigate to forgot password');
    };

    const createAccount = () => {
      // Navigate to registration page
      console.log('Navigate to registration');
    };

    const loginWithFacebook = async () => {
      try {
        // Implement Facebook login
        console.log('Facebook login');
      } catch (error) {
        showToast('Facebook login failed', 'danger');
      }
    };

    const loginWithTwitter = async () => {
      try {
        // Implement Twitter login
        console.log('Twitter login');
      } catch (error) {
        showToast('Twitter login failed', 'danger');
      }
    };

    return {
      formData,
      validationErrors,
      isLoading,
      login,
      forgotPassword,
      createAccount,
      loginWithFacebook,
      loginWithTwitter,
      logoFacebook,
      logoTwitter
    };
  }
});
</script>

<style scoped>
.error-message {
  color: var(--ion-color-danger);
  font-size: 0.8rem;
  margin-top: 5px;
  padding-left: 16px;
}

.invalid {
  border-color: var(--ion-color-danger);
}

.social-login {
  margin-top: 20px;
  border-top: 1px solid var(--ion-color-light);
  padding-top: 20px;
}

ion-card {
  margin: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

ion-card-header {
  text-align: center;
  padding: 24px 20px;
}

ion-card-title {
  font-size: 24px;
  font-weight: 600;
  color: var(--ion-color-dark);
}

ion-card-subtitle {
  font-size: 14px;
  color: var(--ion-color-medium);
  margin-top: 8px;
}

ion-card-content {
  padding: 20px;
}

ion-item {
  --padding-start: 0;
  --padding-end: 0;
  --inner-padding-end: 0;
  margin-bottom: 16px;
}

ion-label {
  font-size: 14px;
  color: var(--ion-color-medium);
  flex: 1;
  text-align: left;
}

ion-input {
  --padding-start: 16px;
  --padding-end: 16px;
  --padding-top: 5px;
  --padding-bottom: 5px;
  --background: var(--ion-color-light);
  --border-radius: 8px;
  margin-top: 22px;
}

ion-checkbox {
  --size: 18px;
  --checkbox-background: var(--ion-color-light);
  --checkbox-background-checked: var(--ion-color-primary);
  --border-radius: 4px;
  --border-color: var(--ion-color-medium);
  --border-color-checked: var(--ion-color-primary);
}

ion-button {
  --border-radius: 8px;
  --padding-top: 16px;
  --padding-bottom: 16px;
  margin: 16px 0;
  font-weight: 500;
}

ion-button[fill="clear"] {
  --color: var(--ion-color-medium);
  font-size: 14px;
}

.social-login ion-button {
  --padding-top: 12px;
  --padding-bottom: 12px;
}

.social-login ion-icon {
  font-size: 20px;
  margin-right: 8px;
}

/* Responsive Design */
@media (min-width: 768px) {
  ion-card {
    max-width: 480px;
    margin: 40px auto;
  }
}

@media (max-width: 576px) {
  ion-card {
    margin: 16px;
  }

  ion-card-header {
    padding: 20px 16px;
  }

  ion-card-title {
    font-size: 20px;
  }

  ion-card-content {
    padding: 16px;
  }
}

/* Dark Mode Support */
:host(.dark-theme) {
  ion-card {
    background: var(--ion-color-dark);
  }

  ion-card-title {
    color: var(--ion-color-light);
  }

  ion-input {
    --background: rgba(var(--ion-color-light-rgb), 0.1);
    color: var(--ion-color-light);
  }

  ion-checkbox {
    --checkbox-background: rgba(var(--ion-color-light-rgb), 0.1);
  }
}

/* Animation */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

ion-card {
  animation: fadeIn 0.3s ease-out;
}

/* Loading State Styles */
ion-button[disabled] {
  opacity: 0.7;
}

/* Error State Styles */
ion-item.invalid {
  --border-color: var(--ion-color-danger);
}

.error-message {
  animation: fadeIn 0.2s ease-out;
}

/* Hover Effects */
ion-button:hover {
  opacity: 0.9;
}

ion-button[fill="clear"]:hover {
  --color: var(--ion-color-primary);
}

.social-login ion-button:hover {
  --background: rgba(var(--ion-color-primary-rgb), 0.1);
}

/* Focus States */
ion-input:focus {
  --background: rgba(var(--ion-color-primary-rgb), 0.1);
}

/* Remember Me Checkbox */
.remember-me {
  display: flex;
  align-items: center;
  margin: 16px 0;
}

.remember-me ion-label {
  margin-left: 0px;
  font-size: 14px;
}

/* Custom Scrollbar */
ion-content {
  --offset-bottom: auto!important;
  --overflow: hidden;
  overflow: auto;
  &::-webkit-scrollbar {
    width: 8px;
  }
  &::-webkit-scrollbar-track {
    background: transparent;
  }
  &::-webkit-scrollbar-thumb {
    background: var(--ion-color-medium);
    border-radius: 4px;
  }
}
</style>