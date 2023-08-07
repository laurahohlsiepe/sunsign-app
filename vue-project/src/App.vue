<template>
<body class="bg-pink-300 font-mono h-screen">
  <header>
    <h1 class="text-2xl text-center pt-12">Sun Sign App</h1>
    <p class="text-md text-center pt-6">Enter your date of birth and find out your zodiac sign and info about it 💓 </p>
    <hr class="my-4 h-0.5 mx-12 border-t-0 bg-neutral-100 opacity-100 dark:opacity-50" />
  </header>
  <main>
    <section class="mt-6">
      <p class="text-center py-2">Enter your birthdate</p>
      <div class="flex justify-center py-2">
        <input type="date" class="border border-gray-300 text-pink-600 text-lg rounded-lg" v-model="birthdate">
      </div>
      <div class="flex justify-center py-2">
        <button class="bg-white rounded-lg p-2" @click="getSunSign">Let's go</button>
      </div>
    </section>
    <section class="pt-12 flex justify-center flex-col">
      <div v-if="zodiacSign" class="text-center">Your Sun Sign is <bold class="font-bold text-fuchsia-950">{{ zodiacSign }}</bold>.</div>
    </section>
    <section class="pt-4 flex justify-center flex-col">
      <div class="text-left mx-32 px-4">{{ getSignInfos() }}</div>
    </section>
  </main>
</body>
</template>

<script>
export default {

  data() {
    return {
      birthDate: '',
      zodiacSign: '',
      zodiacRanges: {
        Aries: ['03-21', '04-19'],
        Taurus: ['04-20', '05-20'],
        Gemini: ['05-21', '06-20'],
        Cancer: ['06-21', '07-22'],
        Leo: ['07-23', '08-22'],
        Virgo: ['08-23', '09-22'],
        Libra: ['09-23', '10-22'],
        Scorpio: ['10-23', '11-21'],
        Sagittarius: ['11-22', '12-21'],
        Capricorn: ['12-22', '01-19'],
        Aquarius: ['01-20', '02-18'],
        Pisces: ['02-19', '03-20']
      }
    }
  },

  methods: {
    getSunSign() {
      const birthdateParts = this.birthdate.split('-');
      const birthMonth = birthdateParts[1];
      const birthDay = birthdateParts[2];

      for (const sign in this.zodiacRanges) {
        const [start, end] = this.zodiacRanges[sign];
        if ((birthMonth === start.substring(0, 2) && birthDay >= start.substring(3)) ||
            (birthMonth === end.substring(0, 2) && birthDay <= end.substring(3))) {
          this.zodiacSign = sign;
          return '';
        }
      }

      this.zodiacSign = '';
    },

    getSignInfos() {
      switch (this.zodiacSign) {
        case 'Aries':
          return 'An Aries Sun is bold, energetic, and assertive. They are natural leaders with a passion for taking initiative and embracing challenges head-on. Independence and a pioneering spirit are at the core of their personality.';
        case 'Taurus':
          return ' A Taurus Sun is grounded, reliable, and values comfort. They have a strong connection to the material world, enjoying pleasures like good food and a cozy environment. Determined and patient, they work steadily toward their goals, and their loyalty is unwavering.';
        case 'Gemini': 
          return 'A Gemini Sun is curious, adaptable, and communicative. They thrive on intellectual stimulation, love to learn, and are skilled at connecting with a wide range of people. Their quick wit and versatility make them engaging conversationalists.';
        case 'Cancer': 
          return 'A Cancer Sun is nurturing, intuitive, and emotional. They are deeply connected to their feelings and those of others, often taking on a caregiving role. Home and family hold special importance for them, and they approach relationships with empathy and sensitivity.';
        case 'Leo': 
          return 'A Leo Sun is confident, charismatic, and radiant. They have a natural flair for the spotlight and enjoy being the center of attention. Their creative and enthusiastic nature makes them natural leaders who inspire and uplift those around them.';
        case 'Virgo':
          return 'A Virgo Sun is practical, detail-oriented, and analytical. They have a strong sense of duty and enjoy helping others in practical ways. Their meticulous approach and problem-solving skills make them valuable team members, and they often focus on improving themselves and their surroundings.';
        case 'Libra':
         return 'A Libra Sun is diplomatic, charming, and values harmony. They seek balance, fairness, and enjoy connecting with others. Known for their social grace, they strive for cooperation and often act as peacemakers.';
        case 'Scorpio':
          return 'A Scorpio Sun is intense, passionate, and perceptive. They have a magnetic presence and delve deeply into matters, often uncovering hidden truths. Emotionally resilient, they approach life with a sense of purpose and are known for their determination and ability to transform themselves and their circumstances.';
        case 'Sagittarius':
          return 'A Sagittarius Sun is adventurous, optimistic, and philosophical. They have a love for exploration and seek meaning through experiences and knowledge. With a free-spirited nature, they embrace change and are often drawn to diverse cultures and ideas. Their enthusiasm and open-mindedness make them inspiring companions.';
        case 'Capricorn':
          return 'A Capricorn Sun is disciplined, ambitious, and practical. They have a strong sense of responsibility and work diligently to achieve their goals. With a structured approach, they value tradition and take pride in their accomplishments. Their determination and ability to persevere through challenges contribute to their success.';
        case 'Aquarius':
          return ' An Aquarius Sun is innovative, open-minded, and humanitarian. They are forward-thinking individuals who often challenge conventions and seek to create positive change. With a strong sense of individuality, they value personal freedom and are drawn to social causes. Their unique perspective and intellectual pursuits make them engaging and inspiring companions.';
        case 'Pisces':
          return ' A Pisces Sun is compassionate, intuitive, and imaginative. They have a deep connection to their emotions and the unseen realms. Often creative and artistic, they express themselves through various mediums. Their empathetic nature leads them to care deeply for others, and they have a tendency to see the world through a unique and dreamy lens.';
        default:
          return ''; 
    }
  }
  }
}
</script>

