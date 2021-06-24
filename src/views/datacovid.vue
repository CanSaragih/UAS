<template>   
    <div id="body">
         <div class="text-xl font-bold pt-10 text-gray-700">DAFTAR NEGARA YANG TERDAMPAK WABAH VIRUS COVID-19
                    <div class="pt-10">
                    </div>
                </div>                
            
                <table class="w-full">
                    <tr>
                        <th class="border-2 bg-gray-100 text-black text-lg font-semibold text-left text-center p-3" >NO.</th>
                        <th class="border-2 bg-gray-100 text-black text-lg font-semibold text-left text-center">NEGARA</th>
                        <th class="border-2 bg-gray-100 text-black text-lg font-semibold text-left text-center" >POSITF</th>
                        <th class="border-2 bg-gray-100 text-black text-lg font-semibold text-left text-center" >MENINGGAL</th>
                        <th class="border-2 bg-gray-100 text-black text-lg font-semibold text-left text-center" >SEMBUH</th>
                    </tr>    
                        <tr v-for="(item, nomor) in data.Countries" :key="nomor">
                        <th class="border-2 bg-gray-100 text-black text-lg font-semibold text-left text-center" >{{ nomor + 1 }}</th>
                        <td class="border bg-white text-lg font-semibold text-left pl-4 p-2">{{ item.Country }}</td>
                        <td class="border  text-lg font-semibold text-center">{{ item.TotalConfirmed | numberFormat }}</td>
                        <td class="border  text-lg font-semibold text-center">{{ item.TotalDeaths | numberFormat }}</td>
                        <td class="border  text-lg font-semibold text-center">{{ item.TotalRecovered | numberFormat }}</td>
                    </tr>     
                </table>         
    </div>        

</template>

<script>
export default {
    data() {
        return {
            countries: {},
            data: {},
            confirmed: 0,
            deaths: 0,
            recovered: 0,
            
        }
    },
    filters: {
        numberFormat(number) {
            return number.toLocaleString();
        }
    },
    methods: {
        getCountries(){
            axios.get('https://api.covid19api.com/countries')
                .then(response => {
                    this.countries = response.data;
                })
        },
        getSummaryData() {
            axios.get('https://api.covid19api.com/summary')
                .then(response => {
                    const data = response.data;
                    this.data = data;
                })
        }
    },
    mounted() {
        this.getCountries();
        this.getSummaryData()
    }
    
}
</script>

<style>
#body {
  font-family: Arial;
  text-align: center;
  color: #2c3e50;
}
</style>