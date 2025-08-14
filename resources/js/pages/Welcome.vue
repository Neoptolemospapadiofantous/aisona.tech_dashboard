<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
import { Button } from '@/components/ui/button';
import AppLogoIcon from '@/components/AppLogoIcon.vue';

// This uses your existing type system and authentication
const { auth } = defineProps<{
    auth: { user: any }
}>();
</script>

<template>
    <Head title="Welcome" />
    
    <!-- Use your design system colors and layout patterns -->
    <div class="min-h-screen bg-gradient-to-br from-background via-muted to-background relative overflow-hidden">
        <!-- Animated Background using your design tokens -->
        <div class="absolute inset-0 overflow-hidden">
            <div class="absolute -inset-10 opacity-20">
                <div class="absolute top-0 -left-4 w-72 h-72 bg-primary/20 rounded-full mix-blend-multiply filter blur-xl animate-blob"></div>
                <div class="absolute top-0 -right-4 w-72 h-72 bg-primary/15 rounded-full mix-blend-multiply filter blur-xl animate-blob animation-delay-2000"></div>
                <div class="absolute -bottom-8 left-20 w-72 h-72 bg-primary/25 rounded-full mix-blend-multiply filter blur-xl animate-blob animation-delay-4000"></div>
            </div>
        </div>

        <!-- Main Content using consistent spacing and typography -->
        <div class="relative z-10 flex items-center justify-center min-h-screen px-6">
            <div class="max-w-4xl mx-auto text-center space-y-8">
                <!-- Logo using your existing component -->
                <div class="mb-8">
                    <AppLogoIcon class="mx-auto size-16 fill-current text-foreground mb-4" />
                </div>
                
                <!-- Use your Button component for consistency -->
                <div>
                    <Button 
                        v-if="!auth?.user" 
                        as-child 
                        size="lg" 
                        class="px-8 py-4"
                    >
                        <Link :href="route('login')">
                            Login
                        </Link>
                    </Button>
                    
                    <Button 
                        v-else 
                        as-child 
                        size="lg" 
                        class="px-8 py-4"
                    >
                        <Link :href="route('dashboard')">
                            Dashboard
                        </Link>
                    </Button>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
@keyframes blob {
    0% {
        transform: translate(0px, 0px) scale(1);
    }
    33% {
        transform: translate(30px, -50px) scale(1.1);
    }
    66% {
        transform: translate(-20px, 20px) scale(0.9);
    }
    100% {
        transform: translate(0px, 0px) scale(1);
    }
}

.animate-blob {
    animation: blob 7s infinite;
}

.animation-delay-2000 {
    animation-delay: 2s;
}

.animation-delay-4000 {
    animation-delay: 4s;
}
</style>