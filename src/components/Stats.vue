<template>
    <div class="text-center mb-3">
        <h2 class="text-3xl font-bold">{{ titulo }}</h2>
        <!-- La math no da? -->
        <!-- <h5>Activos: {{numeroComas(stats.TotalConfirmed-stats.TotalDeaths-stats.TotalRecovered)}}</h5> -->
    </div>
    <div class="grid md:grid-cols-3 gap-2">
        <!-- Caja 1 -->
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Casos</h3>

            <div class="text-2xl mb-4">
                <span class="font-bold">Nuevos:</span>
                {{numeroComas(stats.NewConfirmed)}}
            </div>

            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{numeroComas(stats.TotalConfirmed)}}
            </div>

        </div>

        <!-- Caja 2 -->
        <div class="shadow-md bg-blue-200 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Muertes</h3>

            <div class="text-2xl mb-4">
                <span class="font-bold">Nuevas:</span>
                {{numeroComas(stats.NewDeaths)}}
            </div>

            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{numeroComas(stats.TotalDeaths)}}
            </div>

        </div>

        <!-- Caja 3 -->
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Recuperados</h3>

            <div class="text-2xl mb-4">
                <span class="font-bold">Nuevos:</span>
                {{numeroComas(stats.NewRecovered)}}
            </div>

            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{numeroComas(stats.TotalRecovered)}}
            </div>

        </div>
    </div>
</template>

<script>
export default {
    name: 'Stats',
    props: ['titulo', 'stats'],
    methods: {
        numeroComas(x){
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }
    }
}
</script>

<style>

</style>